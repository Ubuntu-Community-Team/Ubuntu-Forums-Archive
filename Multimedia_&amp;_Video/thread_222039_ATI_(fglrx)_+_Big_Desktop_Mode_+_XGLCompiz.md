---
title: "ATI (fglrx) + Big Desktop Mode + XGL/Compiz ??"
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by pRedat0r on 2006-07-24
Hi,

I am just wondering if anyone has found a way to get XGL/Compiz working with fglrx in a 2 monitor "Big Desktop" mode, where the desktop is spanned across 2 monitors?  I have tried this on and off over the last few months using quinn's repos for compiz and always end up getting errors when it starts (no screens available, etc).

I tried several different methods to get it working and have had no luck (changed gdm.conf to screen #1, etc etc etc).  If anyone out there has this working can you please post what guide you followed, any errors you encountered, and what you did to work through them?

FYI: I have a Radeon 9800 pro card with an LCD on the DVI port and CRT on the VGA port, everything is fully accellerated and working under normal X.

Thanks in advance!

---

### Post by munzli on 2006-08-21
this is a limitation in ati's drivers... the max-texture-resolution is 2048x2048 (afaik), so anything bigger than this will not work! and i don't think ati will raise the max-texture-resolution at any time in the near future... try writing a bug ticket on the ati.com site

---

### Post by bonustracks on 2006-09-13
We're in the same boat.  A solution to this problem would be tremendous.

---

### Post by blitzer on 2006-09-14
This is funny your working on getting 2 monitors going with ATI and I can't get one going :p   Any solutions for ATI 3D for Dapper - I've tried all the other posts :neutral: 

I'm still using Breezy Badger cause 3D just works with it every time (direct rendering) for 3D gaming. ](*,)

---

### Post by leohart on 2007-07-24
Has there been any improvement in this front? Does anyone has fglrx with Big Desktop running Xgl/Compiz (two 1280x1024)?

---

### Post by linkx on 2008-05-02
I have it working. (There is a bug though, see below):

Install Hardy 8.04 final. 

```
sudo apt-get install xorg-driver-fglrx
```

Reboot. Go to System > Administration > Hardware Drivers and enable the driver. Reboot again. 

Then you can either (1) install fglrx control panel and go to Applications > Other > ATI Catalyst Control Center and choose BigDesktop and reboot. 

OR 

```
sudo gedit /etc/X11/xorg.conf
```

Then add this line to the 'Device' section:

```
Option     "DesktopSetup"    "Horizontal"
```

Then Ctrl + Alt + Backspace and log back in. 

This will give you a perfectly working compiz bigdesktop across two monitors without all the annoyances of previous setups (like windows that maximize to span both monitors, or a gnome toolbar that spans both monitors, etc.)

WITH ONE FATAL EXCEPTION: 

XORG/GNOME WILL TOTALLY CRASH WHEN YOU CLICK ON YOUR SECONDARY MONITOR'S DESKTOP BACKGROUND WITH COMPIZ ENABLED. 

Without compiz enabled this does not happen. Someone filed a bug just after Hardy was released. [https://bugs.launchpad.net/ubuntu/+bug/222163](https://bugs.launchpad.net/ubuntu/+bug/222163)

If anyone discovers a way around this it would be great if you let us know!

---

