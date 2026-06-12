---
title: "Rhythmbox and software center don't work"
date: 2013-07-05
forum: Multimedia Software
---

### Post by bovchyk on 2013-07-05
Hi
I have a problem with rhythmbox and ubuntu software center, they are don't starts after I install phyton2.7 for work:( 

outputs in terminal:
bovchyk@bovchyk:~$ rhythmbox
Traceback (most recent call last):
  File "/usr/local/lib/python2.7/site.py", line 548, in <module>
    main()
  File "/usr/local/lib/python2.7/site.py", line 530, in main
    known_paths = addusersitepackages(known_paths)
  File "/usr/local/lib/python2.7/site.py", line 266, in addusersitepackages
    user_site = getusersitepackages()
  File "/usr/local/lib/python2.7/site.py", line 241, in getusersitepackages
    user_base = getuserbase() # this will also set USER_BASE
  File "/usr/local/lib/python2.7/site.py", line 231, in getuserbase
    USER_BASE = get_config_var('userbase')
  File "/usr/local/lib/python2.7/sysconfig.py", line 516, in get_config_var
    return get_config_vars().get(name)
  File "/usr/local/lib/python2.7/sysconfig.py", line 449, in get_config_vars
    import re
  File "/usr/local/lib/python2.7/re.py", line 105, in <module>
    import sre_compile
  File "/usr/local/lib/python2.7/sre_compile.py", line 14, in <module>
    import sre_parse
  File "/usr/local/lib/python2.7/sre_parse.py", line 17, in <module>
    from sre_constants import *
  File "/usr/local/lib/python2.7/sre_constants.py", line 18, in <module>
    from _sre import MAXREPEAT
ImportError: cannot import name MAXREPEAT


How I can fix it?

---

