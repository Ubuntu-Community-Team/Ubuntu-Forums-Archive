---
title: "Multimedia problems - Firefox"
date: 2008-05-29
forum: Multimedia Software
---

### Post by jaklumen on 2008-05-29
I am at my wit's end.

I have followed reassuredlyoffensive's sticky as closely as I can. Yes, I searched other threads-- Flash Player 10 had some videos giving me error messages about not being able to utilize all features.

However, I still have problems with Flash killing Firefox, or causing it to hang-- and I have to force a cold restart (from the machine).

Please do not send me to "Absolute Beginner Talk"... although I'm quite new to Ubuntu, this problem did not seem to fit there.

I was a noob with codecs when I was still in Windows, although I was making a transition to open source there anyway, and so I can keep up with it, somewhat.  But output configurations have me downright confused-- alsa, oss, pulse.  Right now, I have most everything pointing to Alsa that I can find.  So I guess my problem is two-fold: problems with Flash and problems with sound output.

I have upgraded FF from b5 to RC1.  My sound and video apps include Audacity (cannot get capture to work), Gnome MPlayer, gxine player (which gives me segmentation default errors), Totem Movie Player, MPlayer Movie Player, Rhythmbox Music Player, and VLC player (many which were installed per se instructions the stickied thread).

I am most familiar with Audacity and VLC player, having used them in Windows.  I am not running a dual boot, so the keyword is "familiar" and not "Windows".

I will not go too much into hardware unless it's a real issue as far as support.  I am using Realtek hardware for audio, and an Nvidia 7600GT for video.  However, I would like a clear-cut, straightforward answer on the differences between alsa, oss, and pulse-- and what setup I can go with to have the least hassle and fuss possible.  I suspect at least two of them might be in conflict... if two are indeed present.

Read the recent thread on oss... not quite so interested in what is best, but what can have a quick turnaround with few problems.

I'm running a Sempron 3100+ with only 1GB of RAM, and I generally like how quick Ubuntu boots up and generally runs on my machine.  However, multimedia is driving me crazy.  Yes, I'm willing to paste terminal commands, but I want to make sure it's set up RIGHT this time!

---

### Post by Dreamerman on 2008-08-04
I am having the same problem with Firefox, it hangs & cold reboot is needed. Seems to hang on web pages containing multimedia.

Will check out & if successful, I will post it here.

Cheers

---

### Post by NilsE on 2008-08-04
> **Dreamerman said:**
> I am having the same problem with Firefox, it hangs & cold reboot is needed. Seems to hang on web pages containing multimedia.

Will check out & if successful, I will post it here.

CheersThis was an old post and there have been many updates since then.

Try going into Synaptic and remove flashplugin-nonfree and libflashsupport if it is there.  Then reinstall flashplugin-nonfree

---

### Post by tuxxy on 2008-08-04
Sounds like a Flash problem, have you tied using Opera browser as a replacement?

---

