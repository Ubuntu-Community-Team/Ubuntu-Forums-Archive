---
title: "How to ADD Video Card"
date: 2013-12-18
forum: Multimedia Software
---

### Post by Rick St. George on 2013-12-18
It sounds so simple! But in ubuntu (not sure what version I have - should be latest LTS) I want to add a Video Card so I can have a Second Monitor.

My system has onboard video, and when I added a PCI card, on Boot-up it switched to that video card, but would not show anything after BIOS screen. Unplugging the monitor cable would not work, I had to completely remove the PCI video card. Afterward boot-up was normal. This would not be a problem with windows, but HOW do I do it with Ubuntu? 

In the BIOS, under video, there is only PCI and PCI Express. No onboard option, so it must be automatic. 

The video card I am trying to add in the PCI slot is SIS 6326 4M PCI VGA.

Onboard Video:

```

lshw -c video
       display UNCLAIMED     
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: vga_controller cap_list
       configuration: latency=0
       resources: memory:40000000-47ffffff memory:48000000-4801ffff ioport:e800(size=128)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```


Any suggestions?
Thanks!
RSG

---

### Post by Rick St. George on 2013-12-19
I'm thinking of upgrading to Xubuntu 13.10. Download to CD and do a fresh Install. Should I add the 2nd Video (PCI) Card prior to install and let the install configure it?

But, alas ... when I added the PCI VGA card, I get nothing past the boot screen! You see my conundrum?

Any help would be appreciated.
Thanks!
Rick

---

### Post by Yellow Pasque on 2013-12-20
Possibly related: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/1066464](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/1066464)

---

### Post by Rick St. George on 2013-12-20
That makes sense, as every time I log on I get a CRASH REPORT. However, there is still confusion as to which PATCH I need (from -[https://launchpad.net/~dtl131/+archive/mediahacks/+packages](https://launchpad.net/~dtl131/+archive/mediahacks/+packages)), and/or if it is included in Xubuntu 13.10 ? As mentioned above, I'm thinking of a NEW Install using Xubuntu 13.10 - but unsure if this would fix the problem, and IF I should insert the Video Card (along with onboard video) prior to new install of Xubuntu? 

Any suggestions as to how to proceed?
Thanks!
Rick

---

### Post by Yellow Pasque on 2013-12-21
1. Do the install with the onboard
2. Reboot and add my ppa to your sources and it will give the updated SiS driver.
3. Shut down and Insert the card

If the crash was the one in the bug report, all should go well. Does the card have two outputs?

---

### Post by Rick St. George on 2014-01-14
Thanks Temujin, but what is the PPA?  Trashed the computer for now because after installing v13.10, it would not boot at all - or at least no video showed.

Will try again later with another video card, when I have time, but need to know what PPA to add please.

Thanks!

---

### Post by Yellow Pasque on 2014-01-14
Sorry, forgot link: [https://launchpad.net/~dtl131/+archive/mediahacks/+packages](https://launchpad.net/~dtl131/+archive/mediahacks/+packages)

---

