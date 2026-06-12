---
title: "Capture in Kino"
date: 2008-03-16
forum: Multimedia &amp; Video
---

### Post by Krisss on 2008-03-16
Hello! I would appreciate help from anybody who has experience using Kino.

I have been using Ubuntu for about two months (I'm getting to grips with it, but am still essentially a newbie). I'm running Gutsy and I'm using Kino to capture video from my Canon HDV cam. The camera plugs into the ieee 1394 port, and Kino detects the camera (I know this because transport controls from Kino control the playback on the camcorder).

The problem is that when I click 'play' on the camera to begin playback, and then click 'capture' in Kino, the program doesn't capture (no file is outputted or even stored on the storyboard); and the preview screen remains black. (The 'Enable preview during capture' checkbox is definitely selected.) I have tried all three display modes (GDK, XVideo, Redu-XVideo) but am still unsure why the capture won't work.

Something interesting I noticed was that after clicking 'capture', the status bar shows a countdown which reads, "Waiting for DV 10, 9, 8, 7," etc., so that makes me think that the signal from the camera isn't working - even though the AV/C device is detected in IEEE preferences, and, like I said, the Transport Controls are working. This struck me as odd, and I'm not sure how I can have transport controls without having a DV signal. It seems like a paradox to me.

I've searched quite hard for a past thread which deals with this issue - but was surprised that I couldn't find one. Has anybody else ever had this problem, and if so, did you manage to fix it? If you haven't had this problem before, what can I do to get capturing to work properly?

I will really appreciate any replies - even if they're short and seemingly useless. Any thoughts at all will be greatly appreciated. :)

All the best,

Krisss

---

### Post by dad311 on 2008-03-16
You might try running dbgrab from the command line and see if you get any error messages.

Because I was using an VHS player to play all my video, the controls in Kino did not work for me.  I used the command below to run dbgrab directly. 

dvgrab --format raw --duration 2:10:00  /home/<username>/capture

---

### Post by Krisss on 2008-03-16
Hi dad311, thanks for your suggestion. I tried using dvgrab from the command line, and it seems there's the same problem as in Kino:

```
kris@kris-desktop:~$ dvgrab --format raw --duration 2:10:00 /home/kris/capture
Found AV/C device with GUID 0x00008500014e44b7
Warning: Cannot set RR-scheduler
Warning: Cannot disable swapping
"" 551779368960.00 MB 0 frames
Capture Stopped
Error: no DV
```

So, that confirms that the device is found but it isn't receiving DV. I'm somewhat stumped...

---

### Post by dad311 on 2008-03-23
Checkout this[ link]("http://www.kinodv.org/dcforum/dcforum?az=show_topic&forum=102&topic_id=969&mesg_id=969&listing_type=search").

Looks like you might need to upgrade dvgrab to 3.1

---

