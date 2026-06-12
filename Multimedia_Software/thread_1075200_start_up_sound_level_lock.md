---
title: "start up sound level lock?"
date: 2009-02-20
forum: Multimedia Software
---

### Post by baracuda68 on 2009-02-20
Hi.
Using Kubuntu Intrepid, with KDE 4.2, Is there a way to "set" the sound volume, to a fixed level for when I boot up each morning?( I use the kmix applet )

I vary my volume level often throughout the day, but usually forget to turn down the level for when I boot up (LOUDLY) early each morning, disturbing the kids.

Understand what I mean?
Any ideas?

Thanks.:)

---

### Post by dejuren on 2009-04-06
add these two lines to your KDE startup:

amixer -c 0 set Master 10% unmute

amixer -c 0 set PCM 10% unmute

Don't ask me how, this is a second question ;-) Change the volume to the level you prefer.

---

