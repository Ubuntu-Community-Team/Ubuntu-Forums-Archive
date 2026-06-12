---
title: "Sound &quot;sticks&quot; with tty"
date: 2012-10-19
forum: Multimedia Software
---

### Post by Razzeeyy! on 2012-10-19
Hello all, I'm using Ubuntu 12.04 and I like to dig into system and customize it heavily. So when I login in system without lightdm (thru console) sound seem to be "stick" with that first logged tty, and when I switch to my xserver tty (tty7) I hear no sound at all (but I'm able to hear it when switching back to tty1, for ex.).

So how do I disable such behavior and make sound persistent between all tty? Also where should I dig? Because I don't have any idea what is that odd behavior and what service/configuration to blame.

Many thanks.

---

### Post by Razzeeyy! on 2012-10-19
UPDATE: this is pulseaudio "feature"
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/213149](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/213149)

None of suggest solutions there is suitable for me, so I just got away by removing pulseaudio and using alsa, works fine I'm enjoying it :guitar: :3

---

