---
title: "ATI 4850 Hardware Acceleration VAINFO Question ubuntu 10.10 64bit"
date: 2011-02-16
forum: Multimedia Software
---

### Post by viktormadarasz on 2011-02-16
Hi,

I have an ATI 4850 installed under Ubuntu 10.10 64bit with its own propietary driver by Ubuntu 10.10 (the restricted FGLRX one its offering by itself) together with XBVA & LibVa installed also....

Although when i hit **vainfo** in terminal it reports an error about some stuff::::

[I]vainfo
libva: libva version 0.31.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit[/I]


Any workaround to make this thing work?

Thanks,

Viktor

---

### Post by krisofe on 2011-03-05
Hi, 

I'm so disappointed too...
I've tried so possibilities without real results.
I've still HD running but not well (only soft decode...)
So I regret my Ati bought instead of nvidia but my mothercard had Xcrossfire so I decided this one.... Why ;-(

(PS Phenom 965 HD 5700)

---

### Post by Yellow Pasque on 2011-03-05
Try libva from: [https://launchpad.net/~dtl131/+archive/catalysthacks](https://launchpad.net/~dtl131/+archive/catalysthacks)
You should also install the latest Catalyst (remove the old one first):
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)
Finally, make sure you have the latest xvba installed: [http://www.splitted-desktop.com/~gbeauchesne/xvba-video/](http://www.splitted-desktop.com/~gbeauchesne/xvba-video/)
After all that, make sure you have the vlc from the aforementioned catalysthacks repo installed and HD decoding should work. It's not as good as vdpau, but it does take some load off the CPU.

---

