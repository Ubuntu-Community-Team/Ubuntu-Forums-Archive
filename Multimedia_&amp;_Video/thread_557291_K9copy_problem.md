---
title: "K9copy problem"
date: 2007-09-22
forum: Multimedia &amp; Video
---

### Post by jondecker76 on 2007-09-22
Hello

I wanted to get into backing up my DVD collection under linux, but with no success so far.

I installed K9copy and ran it successfully once - that is until I checked an option in the settings to use OpengGL for preview rendering (or something like that). Now it crashes any time I try to run it. I can't find a configuration file anywhere for it, so manually disabling the OpenGL setting isn't a possibility.

here is the output from trying to run from command line:

```

jondecker76@studio-desktop:~$ k9copy
find: /dev/bus/usb/.usbfs/005: Permission denied
find: /dev/bus/usb/.usbfs/004: Permission denied
find: /dev/bus/usb/.usbfs/003: Permission denied
find: /dev/bus/usb/.usbfs/002: Permission denied
find: /dev/bus/usb/.usbfs/001: Permission denied
find: /dev/bus/usb/.usbfs/005: Permission denied
find: /dev/bus/usb/.usbfs/004: Permission denied
find: /dev/bus/usb/.usbfs/003: Permission denied
find: /dev/bus/usb/.usbfs/002: Permission denied
find: /dev/bus/usb/.usbfs/001: Permission denied
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
KCrash: Application 'k9copy' crashing...
KCrash cannot reach kdeinit, launching directly.


```


Does anybody know how I can get this to run again?
Here is what I've tried:
1) Unchecking in add/remove then reinstalling with add/remove... no go
2) Using synaptic and marking for complete removal then reinstalling from synaptic... no go
3) sudo apt-get --purge remove k9copy...... sudo apt-get install k9copy.... no go

its like the configuration file isn't getting wiped (wherever it is located)..


thanks,

Jon

---

### Post by jondecker76 on 2007-09-22
Update--

I did get K9Copy to work - just not from the repos...

I downloaded the newest version's .deb from getdeb.net and all is fine now

---

### Post by wesswei on 2008-01-01
I have the same problem. Thinking openGL would be a better option, I enabled it and never saw the program open up again. I guess I'll have to go the non repo way to get it back again.

---

### Post by wesswei on 2008-01-01
actually, installing from the deb did not do it for me. I instead made a symbolic link. 
```

cd /usr/lib/
ln -s libGL.so.1 libGL.so
```

This seemed to do it. I'm uninstalling the older version and reinstalling the newer one to see if it will work now. I think this is because of the way my ATI card handles the libGL renaming on install.

---

