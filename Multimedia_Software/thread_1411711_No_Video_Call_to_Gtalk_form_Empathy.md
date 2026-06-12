---
title: "No Video Call to Gtalk form Empathy"
date: 2010-02-20
forum: Multimedia Software
---

### Post by llueveYescampa on 2010-02-20
Hi all,

I am running Ubuntu 9.10 in a HP Pavillion dv7t Laptop.
The webcam in the laptop is working fine, but when I try to place a video call to gtalk from Empathy it gets disconnected immediately. The regular chat and the audio calls work fine.

Any ideas if this can be fixed?

Thank you all for any help in advance.

---

### Post by heian on 2010-02-26
Hi,

Nearly the same here.

I updated to ubuntu 10.04 alfa 3 and tried to make a video call to my other WLM account. There was no sign of a video call invitation on the windows machine.

When i tried to start the video call from XP to ubuntu, i hear the ringing sound in Empathy, but there is no button to accept
any incomming call. There is even not any sign on the screen that there is a incomming call. Only the sound.

( Please, let it work in 10.04 LTS )

---

### Post by hunternet93 on 2010-04-05
You need to install the correct drivers. I think these are the packages (but might not be so use the google ;) telepathy-gabble gstreamer0.10-ffmpeg, gstreamer0.10-plugins-farsight, gstreamer0.10, telepathy-stream-engine. In a test I've made recently I got it to work, but I couldn't receive video from the other party. He could see me and we could hear each other. I didn't have all these packages installed though I must have missed some. Maybe I can test again soon.

---

### Post by mjumbewu on 2010-05-15
I was having the same problem until I installed gstreamer0.10-bad-multiverse and gstreamer0.10-ugly-multiverse.  If that works, then you may run into this bug: [https://bugs.freedesktop.org/show_bug.cgi?id=28026](https://bugs.freedesktop.org/show_bug.cgi?id=28026) .  If so, add yourself to the CC list so that the maintainers know it's an issue.

---

