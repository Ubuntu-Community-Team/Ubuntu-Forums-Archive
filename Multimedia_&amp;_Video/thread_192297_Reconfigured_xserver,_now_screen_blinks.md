---
title: "Reconfigured xserver, now screen blinks"
date: 2006-06-08
forum: Multimedia &amp; Video
---

### Post by sasquatch on 2006-06-08
Got a Thinkpad T42 w/ATI 9600 video.
Using it in a docking station with Dell 20" LCD monitor.
Upgraded to Dapper, and it worked for both the laptop LCD *and* the Dell LCD right out of the box! =D> 

The screen resolution would only support 1280x1024 for the Dell, so like an idiot I decided to try reconfiguring the Xserver to upgrade to 1600x1200. I did:

sudo dpk-reconfigure xserver-xorg

and I believe I picked all the defaults, except I selected 1600x1200 of course. And also like an idiot I didn't think to save the xorg.conf file.

Rebooted, and the Dell monitor blinks on and off about once per second, from boot onward. :( 
The laptop LCD still works fine.

Next I did:

sudo dpkg-reconfigure -phigh xserver-org

but it didn't help. Still once-per-second blinking on the Dell LCD. ](*,) 

Maybe it wrote something horrible into the video card's NVRAM?

Help!

---

