---
title: "intel i915 and xorg failure."
date: 2007-07-09
forum: Multimedia &amp; Video
---

### Post by teich on 2007-07-09
Hi All,

I'm having a problem with an intel 915 and xorg.  In the past the x server would occasionally fail to start on boot and give me an error about not finding a device.  Usually /etc/init.d/gdm restart would fix the problem.  Now, I cannot get the xserver running no matter what I try.  I am using the intel drivers (xserver-xorg-video-intel).

lspci output includes:
```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

```

Something curious is happening with the /etc/X11/xorg.conf file.  When the device section is configured as below...

```
Section "Device"
        Identifier        "Intel Onboard somethingorother"
        Driver                "intel"
        BusID                "PCI:00:02:01"
        VideoRam        64000
EndSection
```

... then the xorg error is

```
(WW) intel: No matching Device section for instance (BusID PCI:0:2:0) found.
(EE) NO devices detected.
```

Why is it looking at 0:2:0 when I have told it to look at 0:2:1?  Similarly when I configure the xorg.conf file with 0:2:0...

```
Section "Device"
        Identifier        "Intel Onboard somethingorother"
        Driver                "intel"
        BusID                "PCI:00:02:00"
        VideoRam        64000
EndSection
```

... then the xorg failure message is:
```
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found.
(EE) intel(0): Bad VBT signature
(EE) intel(0): No valid modes.
(EE) Screen(s) found, but none have a usable configuration.
```

I am pretty much clueless at this point.  I have tried dpkg-reconfigure xserver-xorg a few times with no luck.  Can anyone help?

Thanks.

---

### Post by teich on 2007-07-09
Update:  I tried the same with the older xserver-xorg-video-i810 drivers and I am getting the same problems.  That is, I ran

sudo apt-get install xserver-xorg-video-i810
sudo dpkg-reconfigure xserver-xorg
sudo shutdown -r now

... but no xserver.

---

### Post by teich on 2007-07-09
Another strange thing to report.  I have switched back to the xserver-xorg-video-intel drivers.

Using ...
> Section "Device"
        Identifier        "Intel i915"
        Driver                "intel"
        BusID                "PCI:00:02:0"
        VideoRam        64000
EndSection

... I am getting the usual xserver crash BUT there is no reported error, only a warning.  Some clips from the /var/log/Xorg.0.log are below.  All warnings are included.

> X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux Bandicoot 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jul  9 10:54:43 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
...
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000


The full /var/log/Xorg.0.log is at [http://www.teichmans.org/xserverr/Xorg.0.log](http://www.teichmans.org/xserverr/Xorg.0.log) if that helps.

---

### Post by teich on 2007-07-09
Further update:  On a second attempt, without changing anything I was aware of, I am now back to the "Bad VBT signature" error.  

> (WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(EE) intel(0): Bad VBT signature
(EE) intel(0): No valid modes.
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Full output in /var/log/Xorg.0.log is available here: [http://www.teichmans.org/xserverr/Xorg.0.log2](http://www.teichmans.org/xserverr/Xorg.0.log2)

---

### Post by teich on 2007-07-10
Anyone?

Format and start over is the next step.

---

### Post by Triskal on 2007-07-14
I had a similar problem.  Try commenting out or removing your VideoRam line.

---

### Post by teich on 2007-07-15
The xserver has mysteriously started working again, for no reason that is apparent to me.  (I had not changed things in several days).

Anyway, if it happens again I will try commenting out VideoRam.  Thanks for the reply Triskal.

---

### Post by Triskal on 2007-07-16
Great!

---

### Post by teich on 2007-07-16
Kind of.   I'd like to know why.  

Anyway, this computer was pretty much dying anyway.  A new Dell Ubuntu laptop is on the way.  They have some pretty good deals on now, it ended up being $575 off total.

---

### Post by teich on 2007-07-24
.... and that problem is back again, for no apparent reason.  I have not touched anything related to my video drivers or xserver config in ages.

arg.

(edit: no luck with commenting the videoram line out, either.  Thanks for the attempt though.  Apparently no one else has any idea.)

---

### Post by tuesday20102001 on 2007-07-25
> **teich said:**
> Another strange thing to report.  I have switched back to the xserver-xorg-video-intel drivers.

Using ...


... I am getting the usual xserver crash BUT there is no reported error, only a warning.  Some clips from the /var/log/Xorg.0.log are below.  All warnings are included.



The full /var/log/Xorg.0.log is at [http://www.teichmans.org/xserverr/Xorg.0.log](http://www.teichmans.org/xserverr/Xorg.0.log) if that helps.


Sorry if this port is old, but this may help other users with a similar problem. Looking at your PCI bus address, just checking to make sure you have it correct.

Here is what my xorg.conf file looks like (presently stable with generic driver):
Section "Device"
        Identifier      "Intel i915"
        Driver          "vesa"
        BusID           "PCI:0:2:0"
EndSection

not sure why you have so may zeros in the bus address, hope this helps.

---

