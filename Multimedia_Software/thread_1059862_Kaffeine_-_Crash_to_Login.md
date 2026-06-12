---
title: "Kaffeine - Crash to Login"
date: 2009-02-04
forum: Multimedia Software
---

### Post by TransplantedCanuck on 2009-02-04
I've got an interesting sporadic problem...

When watching DVB-T TV in kaffeine (Hauppage Nova-T Lite USB) I normally use fullscreen. Sometimes then when I double click to exit the fullscreen Kaffeine locks up and crashes the system back to the login prompt. But it happens instantly, as if the logout button had been clicked, not slowly like an error and a crash.

Has anyone had this problem before or have an idea where it could come from?

---

### Post by Col-1023 on 2009-02-05
Yes, I have a dvico usb fusion box.

It tunes into channels, but when I try to watch them, I get a garbled picture, it is unwatchable.

If I instantly record the stream, I can then go into the home directory where kaffeine saves the video and watch it there, it is perfect, so kaffeine has a problem with playing the video live.

If I try to change channels, then kaffeine will show the new channel and then crash me back to the login screen.

I don't know what is casuing either of these problems.

My system is an i7 920, Gigabyte X58 DS4 mobo, Radeon HD4870 graphics, and I'm using Ubuntu 8.10-amd64.

I'm fairly sure I have all the required codecs, though I had to download the fluendo mpeg demuxer to watch the video kaff had recorded, fluendo didn't help playing the live stream though.

I tried changing to gstreamer engine, but that didn't work and kaff said it would only play live tv with xine, so I re-set the engine to xine.

Any help with this would be appreciated.

Thanks.

---

### Post by spexs on 2009-04-16
try change option in Kaffeine xine video driver

Kaffeine -> Settings ->xine Engine Parameters -> Video -> driver change from "auto" to "xshm"

this working for me, when Kaffeine logout me from X when I run DVB-T

---

