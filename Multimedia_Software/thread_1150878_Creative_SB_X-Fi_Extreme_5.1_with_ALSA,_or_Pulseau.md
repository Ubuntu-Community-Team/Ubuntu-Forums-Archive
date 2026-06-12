---
title: "Creative SB X-Fi Extreme 5.1 with ALSA, or Pulseaudio...whichever will work."
date: 2009-05-06
forum: Multimedia Software
---

### Post by Jeconti on 2009-05-06
Alright, so I've spent the past few hours reading and researching and trying, and nothing seems to be working just yet, so, I turn to the community.

The card is a Creative SB X-Fi Extreme

I'm running Mythbuntu 9.04. It comes installed with ALSA, so I made sure I had the latest driver and installed it. No difference. I read online that people had better luck reverting to OSS, so I tried it, but at the configure stage, it wants to see libsound 0.9.0 or better. I have libsound2 installed, and I don't know how to make it see that it's valid.

So I gave up and installed Pulse Audio.

Still no 5.1. Saw on the forums that I needed to add default-sample-channels=6 to my daemon.conf. I did. Still no 5.1

Am I still doing something wrong? Or should I not expect 5.1 playback unless I'm playing a DVD or something with a real 5.1 audio stream?

---

### Post by Imortallis on 2009-05-06
why don't you try a DVD with 5.1 audio first to see if anything really is wrong as I don't *think* that the regular system sounds are in 5.1.

---

### Post by Jeconti on 2009-05-06
Hey, so new problem... DVDs won't play. I'll leave this thread open, but looks like I'll have to start a new one too.

---

