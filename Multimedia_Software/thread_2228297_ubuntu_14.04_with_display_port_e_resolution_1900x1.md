---
title: "ubuntu 14.04 with display port e resolution 1900x1200"
date: 2014-06-06
forum: Multimedia Software
---

### Post by ryrbel on 2014-06-06
Hi I had a DVI-D cable connected to the monitor with a native resolution of 1900 x 1200 (24") and everything was wworking fine but now I changed to a display port cable and Ubuntu can't find/set that resolution anymore, in the settings I can only choose between 1024x768 or  800x600.

What could have happened and where should I start to look for a solution ? I'm very new to linux

I'm using an nVidia gtx 750 ti connected to the monitor and under windows (dual boot) it works just fine with the correct resolution

---

### Post by Vladlenin5000 on 2014-06-07
Hi, welcome.

Which driver are you using? Resolution issues due to non detected monitors/connections are often solved using the recommended (tested) proprietary nvidia driver.

---

### Post by ryrbel on 2014-06-07
hi Vladlenin5000

I didn't install any drivers (the additional/proprietary drivers tab is blank) and it was working fine with the dvi-d cable, I only changed to a display port cable and ubuntu can't find the resolution any more. Is a driver needed to use a cable vs. another ?

---

### Post by Vladlenin5000 on 2014-06-08
Yes, it probably is.
I've had many similar experiences and usually what works with HDMI/DVI doesn't with VGA (never tested display port though). I suppose the situation is the same when using other connections.

---

