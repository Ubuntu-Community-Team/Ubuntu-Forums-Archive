---
title: "3d programs freezing when runnind second time."
date: 2007-01-18
forum: Multimedia &amp; Video
---

### Post by frea on 2007-01-18
Hi!
I've installed ubuntu quite recently, had almost no problems with it, somehow i installed the ati drivers ( using some howto on these forums :) ), but recently i discovered a strange behavior. 
1. I run any kind of 3d app ( game, glxgears, self-writen opengl program, anything almost)
 It works fine.
2. I close the program, and run it again ( or an diffrent one ) and now the system completly hangs, ctr-alt-backspace doesn't work, mouse isn't moving, keyboard isn't responding, a total freeze. Only way to get rid of it is to reset the computer.

I am using 64bit ubuntu 6.10 v. ( at least i hope i remember the version correctly ;p ), the graphic card is ati radeon 9600. Don't know what more i should say, so if needed please say :).

Thanks in advance.




Ps. baaah, you can't edit the topic title? :/ I meant "runned" ;p.

---

### Post by carlosfocker on 2007-01-18
Try putting this  
```

Option "KernelModuleParm" "agplock=0"
```

between

```
Driver  "fglrx"
```

and 

```
BusID       "PCI:1:0:0"
```

in your xorg.conf file

---

### Post by frea on 2007-01-19
That wasn't needed, but thanks to your response i discovered that i hat driver "ati" instead of driver "fglrx" in xorg.conf. So after few diffrent ( but trivial ;p ) problems i managed ati-drivers to work, thanks.

---

