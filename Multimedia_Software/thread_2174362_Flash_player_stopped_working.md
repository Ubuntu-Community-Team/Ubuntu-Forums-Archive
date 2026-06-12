---
title: "Flash player stopped working"
date: 2013-09-14
forum: Multimedia Software
---

### Post by kerryhall on 2013-09-14
Firefox 23.0, ubuntu 12.04.3

"The Adobe flash plugin has crashed, try reloading the page" for every flash page I try to view. "no report available"

I have tried:
* purging and then reinstalling the flash player via apt
* tried installing lightspark, didn't work at all
* tried installing flash via tarball
* tried new firefox profile

I'm guessing I have to reinstall my system. Any ideas?

Only thing changed recently: disabled twinview and/or xinerama and went from dual head to triple head setup.

---

### Post by kerryhall on 2013-09-25
Any ideas on this?

---

### Post by Yellow Pasque on 2013-09-26
Did you try clearing the Flash cache and settings? (Make sure you purge lightspark package too).
```
rm -r ~/.adobe ~/.macromedia
```

---

