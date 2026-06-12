---
title: "640x480 Resolution on Radeon X700"
date: 2006-08-17
forum: Multimedia &amp; Video
---

### Post by Schnoid on 2006-08-17
Hey all,

just installed Dapper 64bit on my main machine, 32 bit works fine on my laptop, but I can only get 640x480 screen resolution.

I have a ATI Radeon X700 graphics card, do I need to manually install the Linux drivers to get the card to a usable screen resolution?

Thanks very much.

Schnoid. :)

---

### Post by tseliot on 2006-08-17
I guess there's no need to install the proprietary driver.

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by huwshimi on 2006-10-16
I have had this same problem. Just wondering if you managed to fix it?

---

### Post by igknighted on 2006-10-16
I have an x800, and I have similar issues with the open source driver.  If you are not morally against using the prop. ATI driver, this is what I do:

Boot into recovery mode (or hit ctrl + alt + F1 then login to the text terminal and type init 3 to stop the xserver).  Type the following commands:
```
sudo apt-get update
```
```
sudo apt-get install xorg-driver-fglrx
```
```
sudo aticonfig --initial
```
and finally, assuming there were no errors:
```
reboot
```

boot normally and X should start at your proper resolutions enabled

NOTE: if you are in recovery mode, you do not need to use sudo because you are logged in as root

---

### Post by jkwarras on 2006-10-16
Try to specify the monitor type in the xorg.cong file device section(I had the same problem) like this:

```
Option "MonitorLayout" "LVDS, NONE"
```

or replace NONE by AUTO or CRT or TMDS if you have a secondary monitor/TV.

---

