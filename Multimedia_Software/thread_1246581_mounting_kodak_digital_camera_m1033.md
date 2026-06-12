---
title: "mounting kodak digital camera m1033"
date: 2009-08-21
forum: Multimedia Software
---

### Post by rasatoriva on 2009-08-21
Can anyone tell me how to mount a kodak m1033 easyshare digital camera so I can d/l pictures from internal memory? For the answer i have searched wide and far, but it has left me wishing on a star.

---

### Post by coldReactive on 2009-08-21
See if

```
sudo lsusb | less
```

outputs your camera somewhere while it's plugged in. If it does, tell us the output.

---

### Post by rasatoriva on 2009-08-22
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 04d9:1135 Holtek Semiconductor, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

thats the info ive been given :)

---

### Post by rasatoriva on 2009-08-22
bump :)

---

### Post by myolbug on 2009-09-09
Same issues, here is my output:
Bus 001 Device 013: ID 040a:0598 Kodak Co. Digital Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 045e:00dd Microsoft Corp. 
Bus 002 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Any ideas?

I tried to install the software with Crossover and with WINE, neither worked.

---

### Post by coldReactive on 2009-09-09
Wine isn't supposed to accept drivers.

---

### Post by myolbug on 2009-09-09
Will [this]("http://ubuntuforums.org/showthread.php?t=340271") work?

If so, what info based on the above will work?

---

### Post by agathian on 2009-09-10
rasatoriva,

I dont own a Kodak and dont know if there are any kodak specific nuances. Below are my generic observations and suggestions..

I own a Canon and have used it with multiple versions of Ubuntu over the years. Recently, Hardy and Jaunty, without any problems.

From your lsusb output, it looks like the OS is seeing the device.. either it is not taking the right action or the action fails.

You can set the initial action taken when you connect the camera at  "System->Preferences->Removable drives and Media ". This is for GNOME. There should be equivalent in KDE and others.

Also, in general, you can try doing a "tail -f /var/log/syslog" in a terminal window before connecting the camera to watch the log messages. Alternatively you can check the file after the fact as well.  Posting those messages will help others to troubleshoot as well.

Hope this helps..

---

### Post by DiaitaDoc on 2010-01-04
Hi,

I'm also having issues getting my Kodak M1033 to work in Ubuntu 9.10 on an IBM Thinkpad T41.

"tail -f /var/log/syslog" gives me this:
> 
kernel: [37747.196160] usb 1-4: new high speed USB device using ehci_hcd and address 7
kernel: [37747.330095] usb 1-4: configuration #1 chosen from 1 choice

But then it opens two Camera icons, 2 windows saying "Kodak EasyShare M1033 Camera" asking me what to do, and an error message window that says

> Unable to mount Kodak EasyShare M1033 Digital Camera. Error Initializing Camera: -60: could not lock the device

"lsusb |less" gives me this:
> 
Bus 001 Device 008: ID 040a:0598 Kodak Co. Digital Camera

Any ideas?

---

### Post by Cotopaxi on 2010-01-08
Check out &#8220;gphoto2&#8221;. The link:

[http://www.gphoto.org/proj/libgphoto2/support.php](http://www.gphoto.org/proj/libgphoto2/support.php)

although your camera is not listed there, gphoto does recognize any &#8220;Kodak EasyShare&#8221; camera.

If you have &#8220;gtkam&#8221; (ubuntu) or &#8220;digikam&#8221; (kubuntu), you have an application with a graphical user interface, both are based on &#8220;gphoto2&#8221;.

All 3 programs are in the repositories.

My &#8220;Kodak M340&#8221; is not listed in the &#8220;gphoto2&#8221; list of supported cameras, but I switched the camera ON and in PHOTO SHOOTING MODE, connected it afterwards to the computer and it was recognized immediately by &#8220;digikam&#8221;.

My system is Kubuntu 9.10

Good luck

---

