---
title: "bad bass quality on amarok on Hardy"
date: 2008-06-16
forum: Multimedia Software
---

### Post by fontenot_1031 on 2008-06-16
The bass quality on Amarok under Hardy Heron (OSS instead of ALSA) can be a problem on certain tracks. Is anyone else having a problem with really bad bass quality in Hardy?

---

### Post by Tido on 2008-09-29
> **fontenot_1031 said:**
> The bass quality Hardy Heron 
really bad bass quality in Hardy?

I read an older post about bad mp3 codec what about if you listen to an OGG file?

Rhythmbox with distorted bass problem:
[http://ubuntuforums.org/showthread.php?t=394661](http://ubuntuforums.org/showthread.php?t=394661)
After I read that, I removed ffmpeg
sudo apt-get remove gstreamer0.10-ffmpeg

But I must tell you, that maybe some movie or whatever will not work anymore. But there are other codec's I guess

This works for me with U 8.04 Rhythmbox 0.11.5, Realplayer 10.0.9, tested with two high quality headphones.
Now I boost my headphones to the max and enjoy, like I did with Windows :D

And this is just pathetic: :confused:
The Ubuntu Kernel Team is planning to move to the 2.6.27 kernel for the upcoming Intrepid Ibex 8.10 release.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/183674](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/183674)

---

### Post by Bakon Jarser on 2008-09-29
> **Tido said:**
> 
And this is just pathetic: :confused:
The Ubuntu Kernel Team is planning to move to the 2.6.27 kernel for the upcoming Intrepid Ibex 8.10 release.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/183674](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/183674)

Hopefully this was a problem with ALSA.  Looks like no one has reported having the problem with Intrepid.

I get distorted audio in Amarok and other programs if I keep the program volume at max.  I never set Amarok volume above 80% and this seems to work for me.  I also don't turn the master volume above 80%.

---

### Post by Tido on 2008-09-30
> **Bakon Jarser said:**
> Hopefully this was a problem with ALSA.  Looks like no one has reported having the problem with Intrepid.
I never set Amarok volume above 80% and this seems to work for me.  I also don't turn the master volume above 80%.

U 8.04 is LTS and therefore my note to the bug.

80% yes but NO. I have Intel onboard audio ICH5 like 2'000'000 others, that should run properly unless the hardware is buggy, but with Win XP it works.

Well, I thought I had it working yesterday, even with 100% pcm in [FONT="Courier New"]alsamixer[/FONT], but as expected my .avi files did not play. So I thought I could install the XINE libs, but there I had my bass problem back.
So it would be nice, if someone with a clean U 8.04 install could test my idea.

---

