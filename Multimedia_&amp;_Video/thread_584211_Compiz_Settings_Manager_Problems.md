---
title: "Compiz Settings Manager Problems"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by Valr on 2007-10-20
Hey, I follow the guide on [http://www.linuxparasereshumanos.com/2007/07/10/instalar-compiz-fusion-al-100/](http://www.linuxparasereshumanos.com/2007/07/10/instalar-compiz-fusion-al-100/) to install Compiz-fusion, but I can't seem to open the settings manager. If I try to open it from the terminal the following message appears:
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

Thanks.

---

### Post by jimerickso on 2007-10-21
do you have python installed?

---

### Post by Valr on 2007-10-22
Yep ;(

---

### Post by kklingerman on 2007-10-28
I have this issue too!  Anyone find a solution yet?  Thanks.

---

