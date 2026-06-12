---
title: "Dapper sound problems"
date: 2007-01-09
forum: Multimedia &amp; Video
---

### Post by JulesBl on 2007-01-09
Hi

Updated my system the other day and the sound ceased to work, does anybody know how to fix this?

I am running Dapper 6.06.

The sound card is an iMic usb device.

The start up and shutdown sound occure, but I cannot get any system sounds and Ekiga insists that it cannot access the Alsa channels for the iMic device, that they are busy all the time.

My system was working, anybody got any ideas?

Jules

---

### Post by JulesBl on 2007-01-15
OK found out more.

If I unplug the iMic and re-start the system, plug it back in again, the system finds it and it starts to work again. If I then re-boot I hear the login and startup music and then silence apart from the pc speaker beep for new mail.

Tried unplugging the iMic and then just plugging it back in with no re-boot and it never finds it again, not even the light comes on on that usb channel.

Looks like the root system is taking posesion an never letting go!

Tried running rythmbox using gksudo and it actually return an unkown error which I gues is better than nothing :( 

Jules

---

