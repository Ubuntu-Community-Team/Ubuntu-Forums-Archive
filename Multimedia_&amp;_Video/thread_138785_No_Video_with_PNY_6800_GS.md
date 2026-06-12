---
title: "No Video with PNY 6800 GS"
date: 2006-03-02
forum: Multimedia &amp; Video
---

### Post by Micro Rotors on 2006-03-02
OK here is the place I should have posted my first thread (stupid me) :rolleyes: [First Thread]("http://ubuntuforums.org/showthread.php?t=137720") I went with a PNY 6800GS Overclocked Version and Now I get bars. 

All in all, here is what I have done :

I had a running Breezy and a running Dapper then the new card and Agrrrrrr! :twisted: I get virtical blue bars about 1/8" over the entire screen.

1). I tried to install a fresh Dapper and it stalls on the "configuring xserver.org" every time.

2). I did install a fresh Breezy but I get vertical lines about 1/8" thick throughout the entire screen.

3). Since I did do a complete backup (with the ATI Radeon X300se card) last week I just decided to wipe that entire drive and do a fresh install thinking that since they shared the same swap partition, maybe there was something funny going on there but I don&#8217;t think so. I did a fresh install of Breezy. Again vertical lines about 1/8" thick throughout the entire screen.

4).I tried a live Breezy CD and again vertical lines about 1/8" thick throughout the entire screen.

Each time I did something I tried to fire it up as is first then since it didn&#8217;t I did 
> 
dpkg-reconfigure xserver-xorg 
 
I also read a thread were someone said to do:

>  apt-get install nvidia-glx
apt-get nvidia-settings
nvidia-glx config enable
dpkg-reconfigure xserver-xorg

the **apt-get nvidia-settings** and **nvidia-glx config enable** say command not found.


I am running Breezy i386 and for the dapper I am running the AMD-64 version.

My computer specs:

AMD Athol 3500+
2 gigs ram
PNY NVIDIA 6800 GS (factory over clocked version)

I am just scratching my head over this one. I guess this is the puzzle of the day.

---

