---
title: "Using PVR-150 to capture composite/S-video"
date: 2006-07-27
forum: Multimedia &amp; Video
---

### Post by Tomlin on 2006-07-27
With the help of [http://hyams.webhop.net/mythtv/myth_ubuntu.html]("http://hyams.webhop.net/mythtv/myth_ubuntu.html")  I managed to get my WinTV-PVR-150 set up and running w/mythtv. Actually what I bought the 150 for was to transfer some VHS tapes to DVD. I'm also trying to "dump" some TiVo'd recordings to disk, edit out the commercials and burn to DVD.

I've got the TV connector attached to my antenna and can watch/record OTA channels fine. I've also attached the composite input to my DirecTiVo. Using the 'C' key, I can switch between the TV connector, composite and S-video inputs (the latter 2 giving me the ability to watch whats on my TiVo), however, hitting the 'r' key always records what's on the tuner. Also, even though that's supposed to 'toggle' recording, it never STOPS the recording.

I could always:

ivtvctl -p 1 (to switch to the composite input)
cat /dev/video0 > /tmp/test2.mpg (to capture what's coming in on the composite)

but I'd like to be able to 'see' on my monitor exactly what I'm recording. I guess I'm really looking for a GUI for ivtv. Is there anything out there that I can use?

Any help is appreciated.

Tomlin

---

### Post by reckless2k2 on 2006-08-06
can you post how you got the ovr150 to work in ubuntu?
that would be a big help.

---

