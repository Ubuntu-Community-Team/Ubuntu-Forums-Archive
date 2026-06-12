---
title: "jamu, Mythbuntu 10.04 crash"
date: 2010-05-09
forum: Mythbuntu
---

### Post by Oblong_Cheese on 2010-05-09
Hi all,

When I run jamu -MIV (for interactive session), or with any other options, it crashes with the following terminal output:
```

  File "/usr/lib/python2.6/dist-packages/MythTV/MythBase.py", line 71, in __getattr__
    elif name in self.field_order:
  File "/usr/lib/python2.6/dist-packages/MythTV/MythBase.py", line 71, in __getattr__
    elif name in self.field_order:
  File "/usr/lib/python2.6/dist-packages/MythTV/MythBase.py", line 71, in __getattr__
    elif name in self.field_order:
  File "/usr/lib/python2.6/dist-packages/MythTV/MythBase.py", line 71, in __getattr__
    elif name in self.field_order:
  File "/usr/lib/python2.6/dist-packages/MythTV/MythBase.py", line 71, in __getattr__
    elif name in self.field_order:
  File "/usr/lib/python2.6/dist-packages/MythTV/MythBase.py", line 71, in __getattr__
    elif name in self.field_order:
  File "/usr/lib/python2.6/dist-packages/MythTV/MythBase.py", line 71, in __getattr__
    elif name in self.field_order:
  File "/usr/lib/python2.6/dist-packages/MythTV/MythBase.py", line 71, in __getattr__
    elif name in self.field_order:
  File "/usr/lib/python2.6/dist-packages/MythTV/MythBase.py", line 71, in __getattr__
    elif name in self.field_order:
  File "/usr/lib/python2.6/dist-packages/MythTV/MythBase.py", line 71, in __getattr__
    elif name in self.field_order:
AttributeError: 'VideoTypes' object has no attribute 'field_order'

```

The first part is printed hundreds of times. 

I am using MythTV 0.23, any ideas?

---

### Post by Oblong_Cheese on 2010-05-10
I resolved this issue by doing
```
sudo aptitude update && sudo aptitude remove mythvideo && sudo aptitude install mythvideo
```

I was informed the jamu script needed updating, and to do that I should reinstall mythvideo.

---

