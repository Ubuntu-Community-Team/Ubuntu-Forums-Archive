---
title: "When I plug headphones the spekers don't mute!"
date: 2009-03-24
forum: Multimedia Software
---

### Post by jeko82 on 2009-03-24
Hi,
I can't fix this problem. When I plug in the headphones the speakers don't mute! I have a Fujitsu-Siemens laptop with this sound card:

Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

I am using Ubuntu 8.10.. Is there somebody out there that can help me?

Bye!

---

### Post by ledenjes on 2009-06-26
> **jeko82 said:**
> Hi,
I can't fix this problem. When I plug in the headphones the speakers don't mute! I have a Fujitsu-Siemens laptop with this sound card:

Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

I am using Ubuntu 8.10.. Is there somebody out there that can help me?

Bye!

I added the line "options snd-hda-intel model=targa-2ch-dig" to the file "/etc/modprobe.d/alsa-base.conf".

Now, headphones and speakers share the same volume control.
You get a separate separate window called "Switches" (in Dutch: "Schakelaars") in which you can enable/disable the headphones output. Only now, (in my case) the speakers are muted and cannot be unmuted/enabled, anymore.
I don't care about that, because I don't use sound unless I'm watching a movie or listening to a song, which I only intend to do by using the headphones.

My stuff:
Operating System: Ubuntu Jaunty Jackalope 9.04 AMD64
Computer: Fujitsu-Siemens Amilo Pa1510 (AMD64 processor)
Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (Realtek ALC883)

p.s.: you might wanna have a look at: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/253422?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/253422?comments=all)

---

