# python-package-preset

My preset for a python package that makes importing less of a hassle

Features:

-   You can import anything from anywhere.
-   Import line in code is automatically updated, when the imported file is moved. (tested on vscode)

## Package Directory's structure

```
[Main Parent Dir] <-- folder
├── __init__.py
├── any.py
├── [sub_dir_1] <-- folder
    ├── __init__.py
    ├── any.py
    ├── [another sub dir] <-- folder
        ├── __init__.py
        ├── any.py
|
├── [sub_dir_2] <-- folder
    ├── __init__.py
    ├── any.py
    ├── [another sub dir] <-- folder
        ├── __init__.py
        ├── any.py
```
## `__init__.py` template

- Folder level `0`

```py
# init file for folder level __
import os
import sys
currentdir = os.path.dirname(os.path.realpath(__file__))
sys.path.append(currentdir)
```

- Folder level `1`
```py
# init file for folder level 1
import os
import sys
currentdir = os.path.dirname(os.path.realpath(__file__))
parentdir = os.path.dirname(currentdir)
sys.path.append(parentdir)
```

- Folder level `2`
```py
# init file for folder level 2
import os
import sys
                            # the deeper you go, the more times you'll have to call this function
currentdir = os.path.dirname(os.path.dirname(os.path.realpath(__file__)))
parentdir = os.path.dirname(currentdir)
sys.path.append(parentdir)
```

- Folder level `3` _you probably don't need this?_
```py
# init file for folder level 3, 
import os
import sys
currentdir = os.path.dirname(os.path.dirname(os.path.dirname(os.path.realpath(__file__))))
parentdir = os.path.dirname(currentdir)
sys.path.append(parentdir)
```
