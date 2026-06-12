---
title: "Help with NVIDIA driver"
date: 2006-12-23
forum: Multimedia &amp; Video
---

### Post by BogN on 2006-12-23
Hi,

I have this screen: Samsung SyncMaster 730B
I have this graphic card: GeForce 7600

The native resolution and refresh rate for this screen is: 1280x1024 with 60hz

The only refresh rate that is available to me is: 75...

How can i change it to 60?

---

### Post by tseliot on 2006-12-23
If you installed the latest Nvidia driver (series 9xxx) you should try using nvidia-settings with sudo:
```
sudo nvidia-settings
```

and select the resolution.


If that doesn't work:
Try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD
monitor"):
[url]https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration[/url

---

### Post by BogN on 2006-12-23
Problem solved :-)

I changed the resolution to this: "1280x204_60"

---

### Post by strangedezign on 2006-12-23
> Problem solved

I changed the resolution to this: "1280x204_60"

I had the same problem and used the same solution.  The only problem is the 60hz refresh rate makes my fonts look terrible (they looked great at 75hz).  When I am in windows with the 60hz refresh rate everything looks fine.  I would really prefer to run at the native resolution.  75hz just doesn't look right to me.

BTW

I have subpixel smoothing enabled and am running edgy with the latest nvidia drivers.  Thanks in advance for any help.

---

