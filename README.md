# albertz_PyCParser_Windows
I try to let albertz_PyCParser run on windows

first of all, I change the TAB to 4 spaces. Then 

1. In globalincludewrappers.py, I fixed `libc = ctypes.CDLL('msvcrt.dll')` to instead `libc = ctypes.CDLL(None)`. Else ctypes complain that `expected string or Unicode object, NoneType found`

2. In globalincludewrappers.py, I fixed something like `fdopen` on windows. But I don't know how to let albertz_PyCParser link `fdopen` in C with `_fdopen`

3.  In demos\test_interpreter.py, I mainly renamed the module name to albertz_PyCParser to overcome the name confliction, since there are at least 2 modules with name PyCParser. So I think it is a too bad habit to name a module with a very popular name.

4. However, demos\test_interpreter.py still cannot run

>>> erros so far:
<out-of-scope>: cannot open local include-file 'E:\msys64\home\LOVLJIDY\albertz_PyCParser\demos/test_interpreter.c': [Errno 22] invalid mode ('rb') or filename: './E:\\msys64\\home\\SOMEBODY\\albertz_PyCParser\\demos/test_interpreter.c'

>>>PyAST of main:
EXCEPTION
Traceback (most recent call last):
  File "E:\msys64\home\SOMEBODY\albertz_PyCParser\cwrapper.py", line 33, in __getitem__
    line: raise KeyError(str(k) + " not found in C wrapped state " + str(self))
    locals:
      KeyError = <builtin> <type 'exceptions.KeyError'>
      str = <builtin> <type 'str'>
      k = <local> 'main'
      self = <local> CStateDictWrapper([{}])
KeyError: 'main not found in C wrapped state CStateDictWrapper([{}])'
