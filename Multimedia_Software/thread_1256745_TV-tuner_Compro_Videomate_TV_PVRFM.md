---
title: "TV-tuner Compro Videomate TV PVR/FM"
date: 2009-09-03
forum: Multimedia Software
---

### Post by krishna.988 on 2009-09-03
I can not listen to radio on TV-tuner Compro Videomate TV PVR/FM. I'm using Ubuntu 9.04 and have instaleed gnomeradio.
 
I have followed these instructions: 
1. sudo nano /etc/modprobe.d/saa1734
 
2. added these lines to the file:
 
alias char-major-81 videodev
alias char-major-81-0 saa7134
[FONT=Courier New]options saa7134 card=40 tuner=41 alsa=1[/FONT] 
install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-alsa
 
 
3. sudo rmmod saa7134_alsa && sudo rmmod saa7134 && sudo modprobe saa7134
 
and these instructions
 
[root@mythmaster ~]# cat /etc/modprobe.conf
alias char-major-81-0 saa7134
options saa7134 card=40 tuner=41 alsa=1
alias snd-card-1 saa7134-alsa
options snd-card-1 index=1
options saa7134-alsa index=1
remove saa7134-alsa { /usr/sbin/alsactl store 0 >/dev/null 2>&1 || : ; }; /sbin/modprobe -r --ignore-remove saa7134-alsa
 
 
Can anyone please help me out in listening to radio using gnomeradio and TV using TVtime.? (I have installed TV time and gnomeradio).
I don't have any issues with the TV tuner card as it works good on Windows vista. and also m a newbe to linux world?
 
Note: After running the above commands my realplayer use to quit whenever i tried to play an mp3 or any audio file but after changing the device to OSS on the Hardware tab in realplayer preferences ..it started working..

---

### Post by krishna.988 on 2009-09-04
I solved the issue with these settings card=40 tuner=69 option..Now I'm able to listen to radio with gnome radio.. though kradio throwed some alsa related error messages in gnome..but gnomeradio worked beautifully sound clarity is also good..

---

