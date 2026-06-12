---
title: "&quot;Gallium 0.4 on AMD PALM&quot; doesn't play 1024p 29.97 H.264 video"
date: 2013-08-18
forum: Multimedia Software
---

### Post by 1aunchpad-nct on 2013-08-18
I have a ZBox Nano NXS-AD11 which has an "AMD E-350 APU with Radeon HD graohics x 2" running Ubuntu 13.04 . "About this computer" reports the graphics is "Gallium 0.4 on AMD PALM".  The box is failing to smoothly play h.264 1024p 29.97fps videos in .mov format made with my camera. In "Video" the audio stops after a few seconds while the video continues playing. In VLC the audio plays smoothly but the video breaks up horribly and stutters. In XBMC both video and audio stutter and pause frequently. "System Monitor" shows both CPUs pegged at 100% when VLC is attempting to play the video and 1 pegged at 100% and the other at 70% to 80% when XBMC is attempting to play the video. There is 1.2GB of CPU memory available so it is not a memory problem.  The obvious conclusion is that this little box does not have the power to play 1024p. But there are 2 reasons I think something else is going on: (1) I've found many reports of this box successfully playing 1024p videos (but all of the reporters were using Windows 7) and (2) the Radeon HD supposedly has a hardware decoder for h.264. So it looks to me like Ubuntu/Gallium is not enabling the hardware decoder.  How can I check if the hardware decoder is being used?  Maybe if the System Administration menu hadn't been removed from 13.04 I'd be able to find this on my own....

---

### Post by Yellow Pasque on 2013-08-18
If you're using the open-source driver (which you are), UVD decoding is not enabled by default yet. To verify:

```
sudo apt-get install vdpauinfo
vdpauinfo
```

So you have two options to get hardware decoding assist:
1. Use proprietary driver and XBMC: [http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Using_XBMC_player_.28XvBA.29](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Using_XBMC_player_.28XvBA.29)
2. Install a 3.10 or 3.11 kernel and use this PPA: [https://launchpad.net/~oibaf/+archive/graphics-drivers/](https://launchpad.net/~oibaf/+archive/graphics-drivers/)

I'd recommend the 3.11 kernel ( [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11-rc6-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11-rc6-saucy/) ) and turning on dpm to save power and keep heat down: [https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later](https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later)

---

### Post by 1aunchpad-nct on 2013-08-20
Thank you. I'll try these options.

---

### Post by 1aunchpad-nct on 2013-09-07
When I try to add either the 3.11 kernel ppa or the graphics driver ppa to the package manager the Add Source button remains stubbornly disabled. What are the exact incantions I need?

---

### Post by Yellow Pasque on 2013-09-07
As example:
```
sudo apt-add-repository ppa:oibaf/graphics-drivers
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by 1aunchpad-nct on 2013-09-08
What about the 3.11 kernel ppa? I tried 

sudo apt-add-repository ppa:kernel-ppa/mainline/v3.11-rc6-saucy/

but I got

Cannot access PPA ([https://launchpad.net/api/1.0/~kernel-ppa/+archive/mainline/v3.11-rc6-saucy/](https://launchpad.net/api/1.0/~kernel-ppa/+archive/mainline/v3.11-rc6-saucy/)) to get PPA information, please check your internet connection.

There was nothing wrong with my internet connection.

Also how can I downgrade to the older versions, if I have problems with these?

---

### Post by Yellow Pasque on 2013-09-08
```
sudo apt-add-repository install ppa:kernel-ppa/ppa
```
> Also how can I downgrade to the older versions, if I have problems with these? 
Boot into the regular kernel and use ppa-purge:
```
sudo apt-get install ppa-purge
```

---

