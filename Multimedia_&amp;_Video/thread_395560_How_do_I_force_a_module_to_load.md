---
title: "How do I force a module to load?"
date: 2007-03-28
forum: Multimedia &amp; Video
---

### Post by Lymen on 2007-03-28
Hi 
I'm following the lirc how to: [https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy)
and things seem to be going well... but in the "recording a remote" section it tells you to modprobe the lirc module, and if it does not work to force the module to load.

I got the error, but don't know how to force it to load

any hints?

thanks

---

### Post by tkjacobsen on 2007-03-28
According to modprobe manpages you can ```
sudo modprobe -f module
```

where the '-f' option tells modprobe to force the module to load.

You can see if the module is loaded with  ```
lsmod | grep module
``` 
If that gives any output containing the modulename it is loaded.

---

### Post by Lymen on 2007-03-28
Thanks for the response!
I'll add it to my list of necessary commands

now I just need to figure out where my module went!
I'll keep searching 

thanks again

---

### Post by Lymen on 2007-03-28
just a quick dumb question.

when configuring lirc (the blue screen you get after command: sudo dpkg-reconfigure lirc-modules-source

how does one select the drivers to build.  I don't think I have selected them yet.
I tried "enter"  and the pre selected ones have a * or a star by them 

help if you can
thanks

---

