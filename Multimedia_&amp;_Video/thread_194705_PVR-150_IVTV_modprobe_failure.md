---
title: "PVR-150 IVTV modprobe failure"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by planetmn on 2006-06-11
Hello all,
I am attempting to install MythTV according to Hyams guide and am running into a problem with the ivtv driver.

After installing the IVTV driver, I try to depmod and then modprobe ivtv and I receive the following:

```
david@mythtv:~$ sudo depmod 
david@mythtv:~$ modprobe ivtv 
FATAL: Module ivtv not found.
```

Does anybody know what caused this? Should I just go ahead and reinstall the ivtv drivers?

I tried restarting the computer to see if the module just failed to load, but I get the same response.

Thanks,
dave

---

### Post by planetmn on 2006-06-11
When I "make" the ivtv driver, I see this warning:
```
WARNING: Symbol version dump /usr/src/linux-source-2.6.15/Module.symvers
           is missing; modules will have no dependencies and modversions.
```

Not sure if this is related or not.

-dave

---

