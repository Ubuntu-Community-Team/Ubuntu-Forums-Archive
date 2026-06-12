---
title: "Ubuntu needs to be hard-booted if video is played"
date: 2009-09-19
forum: Multimedia Software
---

### Post by neel_ on 2009-09-19
Hi!

Been planning to move to linux/ubuntu for some time now from win dows. And transition seems to require help.. perhaps lot of it! :)

-Installed ubuntu 8.04.03 LTS on Acer 4736 laptop making it dual boot (XP and Ubuntu)
-Don't have sound at all - found out that perhaps I need to have ALSA driver install/uninstall.
-More importantly though, whenever I play a video file, flv or mpg, in VLC player/MPlayer/GMPlayer/Movie Player, application freezes up and hangs ubuntu and I need to hardboot laptop.

I have installed mediaubuntu packages, latest Adobe flash player (10.something) and ubuntu restricted packages without any success.

If play the same video in real player 11, at least it doesn't hang but continues to give message "Following components are required" : flv or mpg. I have searched net for this message and the suggestions mostly include using some other player or installing mediaubuntu packages and installing ubuntu restricted packages, all of which I have tried.

Can someone help?

Thanks,
Neel.

---

### Post by PrivateSNAFU on 2009-09-19
did you try a 9.04 live cd in the laptop.  From what I have found it seems to be much better at recognising hardware issues.  I think the sound problem is probably causing the crashing in vlc, mplayer etc.

Hope this helps, not really a solution but might help to diagnose the problem.

Keep us informed!

There are some test files in the included folder on the CD i think.

Good luck

---

### Post by utnubuuser on 2009-09-19
Same problem using mplayer?

---

### Post by neel_ on 2009-09-20
Thanks for the repli

@PrivateSNAFU

Unfortunately, I cannot upgrade beyond 8.04 right now - one of the software I am using (vmware server) only supports till 8.04 :(

@utnubuuser

Yes. With every player I am afraid.

I reinstalled 8.04 today and followed the steps about updating VERY religiously - 

- installed ubuntu restricted packages
- updated system through synaptics manager
- installed mediubuntu - almost all packages

Even then, in the end, all other players made ubuntu hung and real player kept on complaining that "flv" component was needed!!

BTW, I am doing all this on Acer 4736 if that raises some red flag..!!

Any suggestion is welcome.

Thanks again,
Neel.

---

### Post by del_diablo on 2009-09-20
Remove pulsaudio, i think it is installed. And it tends to cause a mess.

---

