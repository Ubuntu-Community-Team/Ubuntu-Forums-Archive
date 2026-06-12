---
title: "sound playback problems after install of Karmic with Gnome"
date: 2010-01-05
forum: Multimedia Software
---

### Post by fantan on 2010-01-05
Hi for All!

I did a clean install of Karmic Koala on my computer after the new version came out. After clean installation in the new system I got a lot of problems accoring sound.
My configuration is as follows:
- motherboard: Asus
- processor: Intel(R) Pentium(R) 4 CPU 3.20GHz, 3199.901 MHz
- memory: 1 GB/666 Mhz
- HDD-s: SAMSUNG HD161HJ 140GB
Maxtor 6L080LO 80 GB
- Graphic video card: GeForce 7300 GS
- Sound card: CMI8738

On my computer I have four partitions. 
On 1. of them installed Linux Mint 7 Gloria (Ubuntu 9.04) Hungarian
On 2. of them installed Linux Mint 7 Gloria (Ubuntu 9.04) Russian
On 3. of them installed Kiwi Linux 9.04 (Ubuntu 9.04) with LXDE desktop
All three systems used the same hardware and they are working wery well, without any problem, especially according to sound and video possibilities.

I made a clean install of the new version (Karmic with Gnome desktop) on the 4. partition. Of course before installation I checked the md5sum of downloaded ISO file, checked the burned CD two times. The burned CD is without any defects and errors.
The istallation and the boot process went without problems.

The problems begin when I try to play an mp3 or ogg file with Rhytmbox, Totem, mplayer, Amarok, qmmp, etc. 
The playback starts well, but abruptly the sound gets stumble in one's play, cracks, and at the same time the processor load gets 100%, the playback progress bar in the rhythmbox or totem or amarok or mplayer or qmmp etc. goes to its end quickly. After some time the sound stops or the system totally freezes.
This situation happens again by playback all music files independently with which program play: audacious, qmmp, moc, exaile, amarok, mplayer, vlc, mpg123, mpg321, music123, etc. 
I tried a lot of setup variations in multimedia system setup: Pulseaudio, Alsa, OSS, the result is the same. I uninstalled the pulseaudio totally, but theese problems are abiding.

I can't understand, why theese problems aren't present in my other systems on the same hardware and at the some time they are present in the Karmic Koala.
I don't know at all, how to resolve theese problems, because of that I need all the help from you.
Please help me solve theese problems.

Thanks in advance!

fantan

---

### Post by novalnd on 2010-01-05
maybe you can cek this following url [http://brainstorm.ubuntu.com/idea/23192/](http://brainstorm.ubuntu.com/idea/23192/)

hope it would be help...

---

### Post by fantan on 2010-01-05
> **novalnd said:**
> maybe you can cek this following url [http://brainstorm.ubuntu.com/idea/23192/](http://brainstorm.ubuntu.com/idea/23192/)

hope it would be help...

Thank you very much for your idea!
I checked the URL and I can understand the solutions. I can understand, that the solution #4. is the right solution as written:
"One of the PulseAudio developers, Lennart Poettering, is accusing Ubuntu for not packaging PulseAudio the right way, making people think it's his fault." 
I checked the link:  
[http://0pointer.de/blog/projects/pa-in-ubuntu.html](http://0pointer.de/blog/projects/pa-in-ubuntu.html). 
But I can't find Lennart Poettering's solution and use his patch.
I beg your pardon for my bad English, can you help me where to find the aforementioned patch and how to use it to fix the annoying sound problem in KIarmic?   

Thank you in advance,

fantan

Anybody?

fantan

---

### Post by fantan on 2010-01-06
> **fantan said:**
> Thank you very much for your idea!
I checked the URL and I can understand the solutions. I can understand, that the solution #4. is the right solution as written:
"One of the PulseAudio developers, Lennart Poettering, is accusing Ubuntu for not packaging PulseAudio the right way, making people think it's his fault." 
I checked the link:  
[http://0pointer.de/blog/projects/pa-in-ubuntu.html](http://0pointer.de/blog/projects/pa-in-ubuntu.html). 
But I can't find Lennart Poettering's solution and use his patch.
I beg your pardon for my bad English, can you help me where to find the aforementioned patch and how to use it to fix the annoying sound problem in KIarmic?   

Thank you in advance,

fantan


Anybody?


fantan

---

