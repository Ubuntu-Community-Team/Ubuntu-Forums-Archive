---
title: "VLC occasionally overheats system"
date: 2011-12-21
forum: Multimedia Software
---

### Post by tpheiska on 2011-12-21
I recently did a complete overhaul to my HTPC system, installing a graphics card and switched to using an SSD-drive as root. I also upgraded mythbuntu to the newest version.

I have a very strange problem with my VLC install. Occasionally, maybe one out of three times, when I start VLC something goes terribly wrong and it drives my CPU usage to the maximum, with 'top' showing 194% of usage! The system goes unstable in about 30 seconds and shuts down, I'm guessing due to overheating. I'm able to prevent this by using 'killall vlc' in the terminal but I have to give this command several (5-10) times before VLC is actually stopped.

I've never seen anything like this in Linux and I'm clueless on how to proceed. Re-installing VLC did not seem to help.

---

### Post by inobe on 2011-12-21
vlc version 1.1.12 ?

what are the specs of your htpc..

---

### Post by tpheiska on 2011-12-21
> **inobe said:**
> vlc version 1.1.12 ?


Correct.

HTPC specs = cheapo:

Gigabyte GA-MA78GM-S2H
AMD ATHLON 64 X2 4850E AM2 (45W) BOX 
2x Kingston H 2GB 1066MHZ DDR2
Asus EN210 SILENT

Mythbuntu 11.10

---

### Post by inobe on 2011-12-21
sounds like your gpu isn't doing the work, it's all being processed by your cpu.

why not enable gpu acceleration in vlc...

check out VDPAU as well, see if your configuration is setup properly.

 [http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=EN210+SILENT+vdpau](http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=EN210+SILENT+vdpau)

---

### Post by tpheiska on 2011-12-22
That's what I thought as well. I've disabled the motherboard GPU from BIOS and hooked up the HDMI cable to the graphics card. What really bothers me is the inconsistent behaviour, sometimes the CPU overheats, sometimes not. I'll try and see if VLC settings have something I've missed. I'll also check the VDPAU configs, thanks.

---

### Post by gordintoronto on 2011-12-22
What graphics card? Did you install a driver via Additional Hardware?

VDPau only applies to Nvidia cards.

My VLC is 1.1.4, running Ubuntu 10.10 on my desktop.

---

### Post by tpheiska on 2011-12-25
> **gordintoronto said:**
> What graphics card? Did you install a driver via Additional Hardware?

VDPau only applies to Nvidia cards.

My VLC is 1.1.4, running Ubuntu 10.10 on my desktop.

The card is Asus EN210 SILENT and I installed the Additional Hardware driver through Mythbuntu controls. The VDPau is not familiar to me and I can't seem to find the right config files to modify, Also the Nvidia hardware config tool doesn't seem to have any controls to this matter.

I've tried turning the hardware acceleration on in VLC and also played with the video output formats but I haven't found a working combination. I also think that different video codecs have something to do with the overheating but I haven't been able to confirm. 

The strangest thing is that "killall vlc" only works occasionally, and has to be applied 5-10 times before the process is killed. Sometimes I can't stop the process, even with kill.

---

### Post by gordintoronto on 2011-12-25
Did you install vdpau-va-driver? With Ubuntu 10.10, I installed nvidia-current, which is 260.19.06. I also have libvdpau1 (the last character is a digit) installed.

---

### Post by inobe on 2011-12-25
for your mythbuntu setup, a bunch of info here

[http://www.google.com/search?aq=0&oq=Mythbuntu+vd&sourceid=chrome&ie=UTF-8&q=mythbuntu+vdpau](http://www.google.com/search?aq=0&oq=Mythbuntu+vd&sourceid=chrome&ie=UTF-8&q=mythbuntu+vdpau)

---

### Post by inobe on 2011-12-26
lets just make it simple.

look for mplayer2.

look for smplayer for a frontend.

go into options> preferences> video> output driver, select vdpau.

i get 6% cpu usage from mplayer playing a 1080p res flick.

nvidia card heats up a bit, if you get mouse stutter, the video card is under clocked, go into nvidia settings under powermizer, in preferred mode select max performance.

---

### Post by tpheiska on 2011-12-26
> **inobe said:**
> lets just make it simple.

look for mplayer2.

look for smplayer for a frontend.

go into options> preferences> video> output driver, select vdpau.

i get 6% cpu usage from mplayer playing a 1080p res flick.

nvidia card heats up a bit, if you get mouse stutter, the video card is under clocked, go into nvidia settings under powermizer, in preferred mode select max performance.

Thanks, this seems to help, mplayer plays the files effortlessly. I'll just switch to using it instead of VLC.

---

### Post by inobe on 2011-12-26
i haven't noticed any tearing, i did experience frame drop, that was only for a few seconds and hasn't happened again.

i'm sporting an evga nvidia gtx460 2gb special addition card, if that matters.

---

