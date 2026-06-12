---
title: "Getting Artifacts with some 720p files... VDPAU profile settings?"
date: 2011-03-08
forum: Mythbuntu
---

### Post by killabee44 on 2011-03-08
Hi all,

I am having some issues with video quality. 

Some of the 720p files I play (mkv) give me artifacts with the VDPAU video profile. When I switch to the "high quality" or "CPU" playback video profiles, they play just fine.


Full HD 1080p movies only play well with the VDPAU profile for me, so I would like to use that for everything, rather than keep switching. 

I like that one since it keeps my cpu usage down and works well with fast moving scenes. 

The CPU or the HIGH QUALITY video profiles can't handle 1080p and give me constant freezing. 

Has anyone run into this? Which profile do you think is better? Is there a way to tweak VDPAU?

My Mythbox setup running with the following Hardware:

Motherboard: MB ASUS M3N78-VM
Video Card: Nvidia 9800GT
AMD Phenom Quad-core 9850 2.50GHz Processor
4GB DDR2 800 (PC2 6400) ram

This is all on Myth .22

Thanks!

---

### Post by LowSky on 2011-03-08
create your own profile. set it to use VDPAU at 1080 and for 720 under use ffmpeg & Xvideo.

oh and upgrade to ubuntu 10.10, use mythtv .024 and use the newer nvidia driver. your issues may resolve on their own

---

### Post by novellahub on 2011-03-08
Are the artifacts tearing?  

[http://www.mythtv.org/wiki/VDPAU#Tearing.2FStuttering](http://www.mythtv.org/wiki/VDPAU#Tearing.2FStuttering)

I have this in my xorg.conf

```

   Section "Extensions"
       Option "Composite" "Disable"
   EndSection

```

---

### Post by killabee44 on 2011-03-09
> **LowSky said:**
> create your own profile. set it to use VDPAU at 1080 and for 720 under use ffmpeg & Xvideo.

oh and upgrade to ubuntu 10.10, use mythtv .024 and use the newer nvidia driver. your issues may resolve on their own

Thank for your replies guys..

I upgraded but the problem persists. 

What exactly do I put into the details for the profile? I created one but don't know what to put in it. There is some kind of format that you have to follow...

Thanks!

---

### Post by killabee44 on 2011-03-09
> **novellahub said:**
> Are the artifacts tearing?  

[http://www.mythtv.org/wiki/VDPAU#Tearing.2FStuttering](http://www.mythtv.org/wiki/VDPAU#Tearing.2FStuttering)

I have this in my xorg.conf

```

   Section "Extensions"
       Option "Composite" "Disable"
   EndSection

```

Thanks, Ill try that...

---

