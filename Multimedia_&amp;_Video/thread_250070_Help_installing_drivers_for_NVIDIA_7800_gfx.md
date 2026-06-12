---
title: "Help installing drivers for NVIDIA 7800 gfx"
date: 2006-09-03
forum: Multimedia &amp; Video
---

### Post by Scarlett on 2006-09-03
I followed the instructions for Method 1 - Offline Installation from here using the 64-bit package:  [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper).  

Seemed to be going fine except that I didn't have a glcore to be loaded so I just put a # in front of Load "dri" and moved on.  When I logged out and hit ctrl-alt-backspace it rebooted and I got the nVidia splash screen before Ubuntu loaded but now I can't figure out where the nVidia settings panel went.   

I really need to find it to fix the refresh rate.  The blinking and resizing of the screen is giving me a headache.  Please help.

---

### Post by tseliot on 2006-09-03
About Nvidia-settings:
follow point 6 of Method 1 (not the offline installation this time)


About the refresh rate:
Try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by Scarlett on 2006-09-03
The blinking stopped.  Thank you!!

I added the resolutions and refresh rate to the xorg.conf and changed the horizontal sync and vertical refresh. I guessed on the monitor info since it's so old it's not supported anymore and there's no documentation as to what it should be, but it seems to work ok.  Thanks.

---

