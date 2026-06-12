---
title: "nvidia problems"
date: 2006-08-28
forum: Multimedia &amp; Video
---

### Post by Cure777 on 2006-08-28
I have a nvidia GeForce 6200 graphics card, and I'm having a problem. I use Automatix and Synaptic to install the drivers, but there is still a problem: It still won't let me display at any resolution above 1024x768. I know this is not the highest, seeing as I have a 17-inch monitor, and the native resolution is 1280x1024, which is also what I use on my Windows partition. Does anyone have a solution? Thanks.

---

### Post by croak77 on 2006-08-29
Well you can edit your /etc/X11/xorg.conf and make sure the right VertSync, HorzSync, display depth and resolution is listed.

---

### Post by tseliot on 2006-08-29
Try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

