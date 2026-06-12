---
title: "problem about Installing Intel LAN driver"
date: 2011-06-01
forum: Networking &amp; Wireless
---

### Post by jj_fan_tw on 2011-06-01
Hello Everyone:
 
I am a beginner for using Ubuntu. I encountered an issue while install Intel LAN driver. Tried to find associated documents but in vain. So I post this thread for asking helps. Any possible solutions will be greatly appreciated.
 
 
Under Ubuntu 10.04, try to install Intel LAN driver v1.3.10a
[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&lang=eng)
 
Follow the instruction:
[http://downloadmirror.intel.com/15817/eng/README.txt](http://downloadmirror.intel.com/15817/eng/README.txt)
 
Encounter error while "make install", 
[FONT=&#26032;&#32048;&#26126;&#39636;][SIZE=2]bv@bv-desktop:~/Intel LAN driver/e1000e-1.3.10a/src$ make install[/SIZE][/FONT]
 
[FONT=&#26032;&#32048;&#26126;&#39636;][SIZE=2]make -C /lib/modules/2.6.32-21-generic/build SUBDIRS=/home/bv/Intel LAN driver/e1000e-1.3.10a/src modules[/SIZE][/FONT]
 
[FONT=&#26032;&#32048;&#26126;&#39636;][SIZE=2]make[1]: Entering directory '/usr/src/linux-headers-2.6.32-21-generic'[/SIZE][/FONT]
 
[FONT=&#26032;&#32048;&#26126;&#39636;][SIZE=2]make[1]: *** No rule to make target 'LAN'. Stop.[/SIZE][/FONT]
 
[FONT=&#26032;&#32048;&#26126;&#39636;][SIZE=2]make[1]: Leaving directory '/usr/src/linux-headers-2.6.32-21-generic'[/SIZE][/FONT]
 
[FONT=&#26032;&#32048;&#26126;&#39636;][SIZE=2]make: *** [default] Error 2[/SIZE][/FONT]
 
[FONT=&#26032;&#32048;&#26126;&#39636;][SIZE=2]bv@bv-desktop:~/Intel LAN driver/e1000e-1.3.10a/src$ [/SIZE][/FONT]
 
Try to check and the header files of '/usr/src/linux-headers-2.6.32-21-generic' and it is latest version.
 
How should resolve this problem? Please kindly advise possible solution. Detail step by step instruction will be greatly appreciated.
 
Thank you in advance.
 
JJ

---

### Post by chili555 on 2011-06-01
You generally don't need to build e1000e from a tar.gz; it's already built in to 10.04. In my experience (I have a e1000e-driven device in the computer I'm replying on) the built-in is rock solid and works quite well. What motivated you to build a tar.gz? Is there some problem with the in-kernel version?

Do you have build-essential installed? > Try to check and the header files of '/usr/src/linux-headers-2.6.32-21-generic' and it is latest version.It is the same version as your running kernel?```
uname -r
```

I suspect your only real problem is that ordinary users are not allowed to install software; therefor, you will need:```
[COLOR="Red"]sudo[/COLOR] make install
```However, if there is an underlying problem in your system, a newer driver version is unlikely to fix it.

---

### Post by 8O8AH on 2011-09-15
I too have faced this problem. It is necessary, that the way didn't contain spaces.

---

