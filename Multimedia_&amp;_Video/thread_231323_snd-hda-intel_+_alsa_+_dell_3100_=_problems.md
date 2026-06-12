---
title: "snd-hda-intel + alsa + dell 3100 = problems"
date: 2006-08-07
forum: Multimedia &amp; Video
---

### Post by ghostandride on 2006-08-07
Hi, I'm having a very strange problem. I notice that in my installation of Ubuntu Dapper, if I click on the sound properties, no sound card can be found. Well, if I open a terminal and type:
[INDENT]*aplay -l*[/INDENT]
I get some backtalk like this:
[INDENT]*aplay: device_list:222: no soundcards found...*[/INDENT]
Well, if I try to run lspci I get:
[INDENT]*0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)*[/INDENT]
Amongst other things, so I know it's there and seen (kind of) but just not being "accepted" by the bully OS. I have installed, uninstalled, reinstalled, deinstalled and whatever-else-you-can-think-of-installed alsa and related drivers, oss, libs, utils, whatever. I've done everything that looked remotely useful in these forums, all to no avail. If I try to run alsamixer I get:
[INDENT]*alsamixer: function snd_ctl_open failed for default: No such device*[/INDENT]

Someone please help me before I ninja chop my computer or myself in the face.

](*,) 

Thanks.

---

### Post by ghostandride on 2006-09-07
Not one reply in weeks? Do I have to beg?

---

### Post by xinel on 2006-09-08
Lots of people are having the same problem :(

I have already ninja chopped myself in the face many times.

---

### Post by ghostandride on 2006-09-08
Well, guess who started using Windows on his workstation at work (in a mostly linux environment)? That's right, I did. Because I'm too dumb to figure this out and no one here seems to know anything either. If anyone can figure anything out, I'd greatly appreciate the help. Until then, it's winblows for me at work.

---

### Post by raldz on 2006-10-19
You are not alone.. I have the same problem with my Intel based laptop.. too bad I need sound for much of my work..

---

### Post by raldz on 2006-10-20
Out of urge to stay with Linux, I tried other distros, and was surprised to find Mandriva 2007 suporting my hardware out of the box even on LiveCD.. snd-hda-intel works great, 915resolution was identified properly with the right wide screen resolution and even has AIGLX - XGL enabled and running 3D desktop in LiveCD mode.. This trend in new releases is amazing.. I hope Ubuntu has some big things to come when Edgy is out..

---

