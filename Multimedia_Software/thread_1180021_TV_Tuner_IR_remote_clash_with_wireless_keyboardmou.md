---
title: "TV Tuner IR remote clash with wireless keyboard/mouse"
date: 2009-06-06
forum: Multimedia Software
---

### Post by lorstan on 2009-06-06
From what I have seen in this forum, I know there are many people (like me) trying to get remotes working with tuner cards. I thought I would post a minor success I have had in my own struggles, in case it helps someone.

My situation is that Jaunty won't recognise the IR remote within my Hauppauge NOVA-TD USB tuner card, so I have been trying to get a separate IR remote working instead. This is a DVICO FusionHDTV remote with a dedicated USB receiver (I'm not using the DVICO tuner, I'm still using the Hauppage tuner). This also was not being recognised by anything except lsusb - for example, irw would not echo key presses. I've reinstalled and reconfigured LIRC so many times I have lost count.

Anyway, I ended up (after a long, long time) working out that it clashed with my wireless keyboard/mouse (Logitech EX100).  When I use a wired keyboard and separate wireless mouse (Microsoft), irw successfully echoes keypresses from the DVICO remote; back when I used the Logitech combination keyboard/mouse, irw returned nothing. I suspect this is something to do with hal but that's just a guess.

Some of you would probably have worked this out more quickly, but I'm new to Ubuntu. I still have a few issues but at least I am now getting somewhere! I hope this helps someone.

---

