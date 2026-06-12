---
title: "No sound over HDMI"
date: 2008-12-28
forum: Mythbuntu
---

### Post by NautiusMaximus on 2008-12-28
Hi All

I've managed to connect up my HTPC to my TV using an HDMI connection, and the picture is just fine. Trouble is, there's no sound.

I'm using Mythbuntu 8.10 and a Gigabyte GA-M78SM-S2H motherboard. I have no separate graphics card or sound card: the motherboard is doing both. I've checked the motherboard BIOS settings and audio over HDMI is, in theory, enabled.

Any ideas where to start? 

Thanks
NM

---

### Post by ian dobson on 2008-12-28
Hi,

I'm also interested in this. I'm about to buy a new HD-TV and am wondering about audio out.

What do you see when you go to the terminal and do a 
aplay -l

Regards
Ian Dobson

---

### Post by netslacker on 2008-12-29
That mobo has nvidia graphics and last I checked their drivers did not support audio over HDMI in linux.

You may want to do some google searching to see if that has changed recently but I don't believe so. 

I currently use the dvi/hdmi cable and a seperate analog audio cable to the TV.  This works well and is hassle free.

---

### Post by JugeHuge on 2008-12-29
This might help you out.
[No sound over HDMI with ga-ma78gm-s2h AMD 780G motherboard]("http://www.gossamer-threads.com/lists/mythtv/users/333112#333112")

---

### Post by patrick0605 on 2008-12-30
> **JugeHuge said:**
> This might help you out.
[No sound over HDMI with ga-ma78gm-s2h AMD 780G motherboard]("http://www.gossamer-threads.com/lists/mythtv/users/333112#333112")


Probably not, since his MOBO has the nVidia chipset and not the AMD/ATI.

Anywho, I thought I read somewhere that nVidia is slowing starting to support audio over HDMI, try taking a look on there site, I'm almost certain I read that they have.

---

### Post by JugeHuge on 2008-12-31
If you read the guide you might find out that it's pretty much generic guide and has nothing to do with ati or nvidia.. Nothing hardware specific..

---

### Post by bmwman on 2009-01-01
I also have Gigabyte mobo and was trying to have audio over HDMI. I gave up on it and use SPDIF now instead but the last post in my thread has info how to get it to work. Take a look.

[http://ubuntuforums.org/showthread.php?t=903371&page=3]("http://ubuntuforums.org/showthread.php?t=903371&page=3")

---

### Post by mr_raider on 2009-01-02
I got it working on Asus m3n78-vm. First step is to enable the latest proprietary drivers from nvidia. The default 177.80 version with Ubuntu 8.10 is enough.

Then you need to update alsa to 1.018a:

[http://ubuntuforums.org/showthread.php?t=962695&highlight=alsa+update](http://ubuntuforums.org/showthread.php?t=962695&highlight=alsa+update)


At that point you reboot, and when you type
 
```

aplay -l
```

You should see HDMI on hardware 0.3.

Then use synaptic to get the package called gnome-alsamixer and run it from the command line

```

gnome-alsamixer
```

Go through all the outputs and make sure that iec958 and all the sliders labelled digital or PCM are enabled, maxed and not muted.

After that, it dpends on whether you have pulse audio installed or not. In ubuntu (gnome) it's fairly simple by installing a package called asoundconf-gtk. In Mythbuntu, I don't know, but someone else can tell you how to set the default output in Myth or edit the .asoundrc file. If you use gnome, I'd be happy to tell you how it works.

---

### Post by rodercot on 2009-01-02
I wrote a guide for this on the XMBC forums. It is pretty generic and should work with any Nvidia chipset board. I used the 180.11 Nvidia Beta drivers at the time and have since upgraded to 180.18 and all is still fine and that driver seems stable. I also setup the Asus M3N8-VM as well as the new Asus P5N7A-VM. Both use a generic 10de Mcp78a on the m3n and mcp7a on the p5n7a. I can pass everything except uncompressed multi-channel.

 here is the link

 [http://xbmc.org/forum/showthread.php?t=42183](http://xbmc.org/forum/showthread.php?t=42183)

 Good Luck.

 Dave

---

### Post by bone2006 on 2009-01-06
ubuntu 8.10 followed these instructions and audio is playing on my TV with HDMI can the same motherboad you have
[http://www.mediaboxblog.co.uk/blog1.php/2008/08/15/howto-audio-over-hdmi-with-the-hd3200-rs](http://www.mediaboxblog.co.uk/blog1.php/2008/08/15/howto-audio-over-hdmi-with-the-hd3200-rs)

It plays with mplayer, but I can't get vlc to play it yet, not sure why?

---

### Post by mr_raider on 2009-01-06
Assuming you are using pulseaudio, run the pavucontrol utility while VLC is playing, and redirect the output to the HDMI sink.

---

### Post by juicedM3 on 2009-01-09
I just posted this to the Ubuntu forums.  I figure I'd cross post since I included MythTV settings and hope that it helps someone out.

[http://ubuntuforums.org/showpost.php?p=6519758&postcount=36](http://ubuntuforums.org/showpost.php?p=6519758&postcount=36)

Justin

Mobo:    Asus M3N78 PRO
Chipset: nVidia GeForce 8300
Audio:   Realtek ALC1200

---

### Post by NautiusMaximus on 2009-01-11
> **mr_raider said:**
> I got it working on Asus m3n78-vm. First step is to enable the latest proprietary drivers from nvidia. The default 177.80 version with Ubuntu 8.10 is enough.

Then you need to update alsa to 1.018a:

[http://ubuntuforums.org/showthread.php?t=962695&highlight=alsa+update](http://ubuntuforums.org/showthread.php?t=962695&highlight=alsa+update)


At that point you reboot, and when you type
 
```

aplay -l
```

You should see HDMI on hardware 0.3.



OK, I've updated my NVIDIA drivers. I'm using 177.82.

I've also followed the instructions on the link you gave to update the Alsa drivers. At least I think I did, but as I'm a bit of a Linux newbie I can't guarantee I didn't screw up somewhere.

But when I type
```

aplay -l
```

I don't see anything about HDMI. This is the output I get:

> **** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Any ideas where to go from here?

Many thanks
NM

---

### Post by NautiusMaximus on 2009-01-17
Bump

---

### Post by ikke2808 on 2009-01-17
Hi 

This afternoon I found this:
[http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)

My hardware:
Motherboard: Gigabyte GA-M78SM-S2H
CPU: AMD Phenom 8650 Triple-Core 2,3 GHz
RAM: 4 GB, Corsair TWIN2X 6400 DDR2
Video Card: Onboard GeForce 8200
Sound Card: Onboard
HD: 1 TB Samsung SpinPoint F1
Remote: TechnoTrend on card (not fully working yet)
Tuners: Technotrend C-1501-CI
Country: The Netherlands
TV provider: Ziggo
TV signal type: DVB-C

And it worked! I ran the script and after the reboot my audio worked!

Now I want my remote to work! Any one results on your TV remote via the HDMI cable? I am told this can work...

Cheers.

---

