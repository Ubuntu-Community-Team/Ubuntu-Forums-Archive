---
title: "a recent update has caused my IEC958 output to stop working"
date: 2011-02-01
forum: Multimedia Software
---

### Post by deruberhanyok on 2011-02-01
I've recently noticed that my IEC958 digital audio output has stopped working. The short version of why I didn't notice this immediately is that I have two simultaneous audio outputs from my system to my speakers and I hadn't realized the IEC958 output wasn't in use.

After messing around with a few settings to no avail, I remembered that I'd recently run update manager (this had to be within the last two weeks) and thought this might be the cause.

I have just booted to a 10.10 install disc and verified the IEC958 output works fine there.

Unfortunately I'm not sure which of the recent updates could have caused this problem. Before I submit a bug report on launchpad I was hoping anyone here might have a suggestion as to where to look to figure this out.

I'd recently seen [this thread]("http://ubuntuforums.org/showthread.php?t=1678594") and [this thread]("http://ubuntuforums.org/showthread.php?t=1677903") which lead me to believe it may have been a recent kernel update.

What's my best course of action to determine the problematic update?

[edit]

In case anyone needs the info, I'm running Ubuntu 10.10 64 bit on a system with an Intel DH57JG motherboard. Using the HDMI output to a TV, with a separate optical audio cable to my speakers.

Also, I've attempted using all of the available digital audio output options in the sound preferences panel and I've also installed gnome-alsamixer and tried enabling/disabling every digital output listed there as well. None of these got the optical output working again.

[edit edit]

Oh, and this would have been in either the maverick-security or maverick-updates repositories, not proposed or backports.

---

### Post by deruberhanyok on 2011-02-01
Found it. That was quick! I was just reading about trying to boot with a previous kernel, so I went back and tried 2.6.35-24 and the output is working again. For anyone with a similar problem, hold SHIFT at boot to get the GRUB boot menu, and try selecting the previous kernel.

I noticed that a 2.6.35-26 is sitting in proposed, so I tried installing that but it still doesn't work. I'll submit a bug report now.

[edit]

Submitted to launchpad as [bug 711598](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/711598)

---

### Post by johnrunsubntlnx on 2011-02-05
sub'd

i have the same problem, waiting for fix

---

### Post by xinel on 2011-02-06
same problem, waiting for fix as well
best i can do atm is use my headphones attached to my monitor that outputs sound from hdmi

---

### Post by johnrunsubntlnx on 2011-02-14
any updates on the issue yet?

---

### Post by tweakt on 2012-02-04
Same problem here. Patiently awaiting a fix.

To make matters worse, the next day the analog output stopped working too! I thought I was losing my mind. Turns out it was because I'd updated to the latest unstable Chrome and sound didn't work at all there, Firefox is still fine.

Other native apps though don't seem to work, like mplayer. I'm running Xubuntu and I haven't been at all happy at the level of integration (no pulseaudio mixer/settings panels).

---

