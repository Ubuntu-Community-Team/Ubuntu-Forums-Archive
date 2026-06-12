---
title: "Can't start X with ATI radeon X550"
date: 2006-01-17
forum: Multimedia &amp; Video
---

### Post by dierre on 2006-01-17
Hello...

I just bought a Sapphire ati radeon X550 graphics card but unfortunately I can't make X work with that... (X won't even start).

Actually, x complains that:

```
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Radeon X600 (RV370)".
(WW) ATI:  PCI Mach64 in slot 1:0:1 could not be detected!
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(EE) No devices detected.

Fatal server error:
no screens found
```

I found some threads that dealt with installing with new drivers, but for now I don't feel like installing new drivers for squeezing maximum performances, I would simply like it to work nicely...

I'm using ubuntu 5.10 for 64 bit processors.

Many many many thanks to everybody who could give me a hint. I attach to this post the output of lspci, xorg.conf, xorg.0.log. I had to cut parts of the log file otherwise the post attachment wouldn't get accepted... I hope I trimmed the right parts.

---

### Post by christhemonkey on 2006-01-17
there has to be some way of getting those attached files with line breaks, was really difficult to find relevant sections!
Thanks to fireonyx for this:


Originally Posted by fireonyx
> The ATI driver has been recently updated, and you have to install the driver, which you can find out here somewhere. In the meantime, edit the /etc/X11/xorg.conf and under the graphics card, put the option "noaccel". Here is the code : 
Section "Device"
Identifier "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
Driver "ati"
BusID "PCI:1:5:0"
Option "NoAccel"
EndSection 

---

### Post by dierre on 2006-01-17
Thank you for your help

Btw... does "Installing new driver" mean following instructions at : 
[http://ubuntuforums.org/showthread.php?p=408111](http://ubuntuforums.org/showthread.php?p=408111) ?

I tried (you know, I don't really feel like setting "Noaccel" on a card I bought yesterday :-P )
and now it complains that:

```
(II) LoadModule: "fglrx"
(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
Duplicate symbol rol_long in /usr/X11R6/lib/modules/drivers/fglrx_drv.o
Also defined in /usr/X11R6/lib/modules/linux/libint10.a

Fatal server error:
Module load failure
```


Thank you again...

---

### Post by dierre on 2006-01-17
Ups... I should read ALL OF the HOWTO...
Now I'm trying the fix :-)

---

### Post by dierre on 2006-01-17
I tried the fix for the libint problem...

Now I have another problem :-(
```

(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.16.20
(II) ATI Proprietary Linux Driver Release Identifier: @@UNRELEASED_AND_UNSUPPORTED_DRIVER@@
(II) ATI Proprietary Linux Driver Build Date: Aug 16 2005 00:12:33
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.16.1-driver-lnx-x86_64-206829
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(EE) No devices detected.

Fatal server error:
no screens found
```

Thank you for your help.....

---

### Post by christhemonkey on 2006-01-19
Sorry have been busy with exams!
Hmmm....
sudo aticonfig --initial
or
sudo fglrxconfig
let me know!

---

### Post by christhemonkey on 2006-01-19
Or take al look at this thread:
[http://ubuntuforums.org/showthread.php?p=423584#post423584]("http://ubuntuforums.org/showthread.php?p=423584#post423584")

---

### Post by dierre on 2006-01-25
So... I tried everything. :-)
The only way I managed to make it work was by downloading and installing the new ATI drivers has explained in [http://ubuntuforums.org/showthread.php?p=423584#post423584](http://ubuntuforums.org/showthread.php?p=423584#post423584)

Now almost everything seems to work fine; the only thing not working is that from the main "applications" menu, if I try to launch "ATI Control" then nothing happens... any suggestion on how to handle this please? :-)

---

