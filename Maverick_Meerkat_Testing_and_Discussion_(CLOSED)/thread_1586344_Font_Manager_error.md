---
title: "Font Manager error"
date: 2010-10-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by vaskark on 2010-10-01
Font Manager does not start for me. This is what I get at the CLI:

```
$ font-manager
Traceback (most recent call last):
  File "/usr/bin/font-manager", line 104, in <module>
    main()
  File "/usr/bin/font-manager", line 93, in main
    from main import Main
  File "/usr/share/font-manager/main.py", line 40, in <module>
    import core
  File "/usr/share/font-manager/core/__init__.py", line 849, in <module>
    os.symlink(USER_LIBRARY_DIR, join(USER_FONT_DIR, 'Library'))
OSError: [Errno 1] Operation not permitted

```Anyone else seeing this and have a solution?
Thanks.

---

