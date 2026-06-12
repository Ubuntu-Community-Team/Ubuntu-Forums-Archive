---
title: "Webcam with Ekiga"
date: 2007-08-28
forum: Multimedia &amp; Video
---

### Post by evolve on 2007-08-28
I got my Logitech QuickCam Deluxe (09c1) semi-working with Ekiga.

I can see myself using the UVC driver from [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/), but as soon as I try to connect, the connection fails and I get a webcam error. The video goes out and I can't seem to recover it.

I can see myself again after a restart, but the same error happens every time I try to connect.

I'm using the latest version of Ekiga (2.0.9), which is supposed to play nice with UVC.  Did I install the driver wrong?

---

### Post by evolve on 2007-08-28
FINALLY!  I think I found a permanent solution to getting the 09c1 Logitech QuickCam Deluxe working with Ekiga.

after installing the UVC driver, I edited the options file:

**sudo gedit /etc/modprobe.d/options**

then added the following line to the end:

**uvcvideo trace=15**

And now it works!  This leads me to one other question though:

My girlfriend (who's using the Windows 2.0.9 beta Ekiga) and I can hear each other (both on ekiga.net sip).  We can't see each other though.  We both can see streams of ourselves, but not the other person.

How can we stream webcams between each other?

---

### Post by YannickDefais on 2007-08-29
Hi,

Weird you have sound but video...

Check you have the video support activated in both Ekiga in Edit -> Preferences -> Video codecs -> Enable video suport

Then each of you should try to call sip:500@ekiga.net
It is an echo test with video. 
Be sure you can select View -> Remote video (or both) *during* the call.

If it works for both of you, then you should try to call each other.

Regards,
Yannick

---

### Post by evolve on 2007-08-29
Thanks for your response.  We tried it again last night after I had fiddled with the the UVC driver and it just started working.  I have no idea what I did, but I'll take it.

Trouble is, sometimes the webcam video will work, and sometimes it won't.  It tends to work again after I exit Ekiga and do the following in the terminal:

[B]sudo rmmod uvcvideo
dmesg | grep uvc[/B]

I already have **modprobe uvcvideo trace=15** in my uvc options file, so I get an error every time I sudo that in the terminal.

I'm not entirely sure what those two lines do for me, but is there some way I could make the UVC driver play nicer with Ekiga so I can get it more consistently working?

---

