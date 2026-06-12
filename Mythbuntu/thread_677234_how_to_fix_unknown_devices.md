---
title: "how to fix unknown devices"
date: 2008-01-24
forum: Mythbuntu
---

### Post by lime4x4 on 2008-01-24
fresh install of mythbuntu

 1
 2
 3
 4
 5
 6
 7
 8
 9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30

	

john@john-mythtv:~$ lspci
00:00.0 Host bridge: nVidia Corporation Unknown device 07c0 (rev a2)
00:00.1 RAM memory: nVidia Corporation Unknown device 07cb (rev a2)
00:01.0 RAM memory: nVidia Corporation Unknown device 07cd (rev a1)
00:01.1 RAM memory: nVidia Corporation Unknown device 07ce (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 07cf (rev a1)
00:01.3 RAM memory: nVidia Corporation Unknown device 07d0 (rev a1)
00:01.4 RAM memory: nVidia Corporation Unknown device 07d1 (rev a1)
00:01.5 RAM memory: nVidia Corporation Unknown device 07d2 (rev a1)
00:01.6 RAM memory: nVidia Corporation Unknown device 07d3 (rev a1)
00:02.0 RAM memory: nVidia Corporation Unknown device 07d6 (rev a1)
00:03.0 ISA bridge: nVidia Corporation Unknown device 07d7 (rev a2)
00:03.1 SMBus: nVidia Corporation Unknown device 07d8 (rev a1)
00:03.2 RAM memory: nVidia Corporation Unknown device 07d9 (rev a1)
00:03.3 Co-processor: nVidia Corporation Unknown device 07da (rev a2)
00:03.4 RAM memory: nVidia Corporation Unknown device 07c8 (rev a1)
00:04.0 USB Controller: nVidia Corporation Unknown device 07fe (rev a1)
00:04.1 USB Controller: nVidia Corporation Unknown device 056a (rev a1)
00:08.0 IDE interface: nVidia Corporation Unknown device 056c (rev a1)
00:09.0 Audio device: nVidia Corporation Unknown device 07fc (rev a1)
00:0a.0 PCI bridge: nVidia Corporation Unknown device 056d (rev a1)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 056e (rev a1)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0e.0 IDE interface: nVidia Corporation Unknown device 07f0 (rev a2)
00:10.0 VGA compatible controller: nVidia Corporation Unknown device 07e0 (rev a2)
01:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
01:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 14)
john@john-mythtv:~$ lsipci

---

### Post by ubnewbie2 on 2008-01-24
Wild guess here, try installing the nvidia proprietory drivers?

---

### Post by lime4x4 on 2008-01-24
I tired that with the restricted device manager and it will only install the video drivers which don't work anyway

---

### Post by Cal55 on 2008-01-27
I'm having similar problems with my MSI P6NGM Motherboard, which has an Nvidia NForce MCP73 (possiby same as NForce 630i) chipset.

It seems that like mine, your devices do not yet appear in the file : /usr/share/misc/pci.ids.  This is updated by :-

```
 sudo update-pciids
```

However, that just fetches the most recent version of pci.ids from here I believe : [http://pci-ids.ucw.cz/](http://pci-ids.ucw.cz/)

If you look at the NVidia section you'll see that the relevant devices are either not yet listed or are under review. : [http://pci-ids.ucw.cz/iii/?i=10de](http://pci-ids.ucw.cz/iii/?i=10de)

However, I haven't yet tracked down what the exact implications of this are.  I've been having problems getting the onboard sound to work with my motherboard, but the ethernet (also shown as unknown device) seems to work fine.

What exact problem(s) have you got?

Hope this helps

Chris

---

### Post by lime4x4 on 2008-01-27
vide didn't work right and the restricted drivers made it worse. I got my video working by installing the nvidia's 169 drivers. Sound didn't work either. Got that working by installing the linux-backports-module. Everything else apears to be working fine at the moment.

---

### Post by mattcole on 2008-01-28
lime4x4:

Did you have to run any other configuration besides installing linux-backports-modules to get sound going?  I believe I'm stuck after installing those, because I appear to have the same chipset (NVIDIA nForce e-7150/630i), but I still don't have sound after installing the backported modules and trying to reconfigure alsa...

thanks,
Matt

---

### Post by Cal55 on 2008-01-28
I may be on the wrong track.  But my further research on this suggests that this chipset is NOT (yet??) supported in the current (or probably the upcoming in 8.04) kernel in Ubuntu 7.10.

See:- [http://www.linuxquestions.org/questions/linux-general-1/pci-device-names-confusion-616627/]("http://www.linuxquestions.org/questions/linux-general-1/pci-device-names-confusion-616627/")
...for a (bit over my head) discussion of how the linux kernel tries to configure un-specified devices.  I think we're in this area at the moment as there's no suggestion that the NForce MCP73 / 630i is fully recognised.

Personally, installing the backport crashed my pc, and the current Alpha of 8.04 wouldn't load a GUI.

So, I'm trying to track down if/how/when any kernel, and then the Ubuntu one will properly support this chipset.

Incidentally, when I loaded 8.04 it loaded a sound driver/module - the hd_intel one (to be found in the Linux legacy drivers from Nvidia. [http://www.nvidia.com/object/linux_nforce_1.23.html]("http://www.nvidia.com/object/linux_nforce_1.23.html") ).   But 7.10 doesn't seem to load this.  Perhaps worth trying to load that somehow?  

I resorted to an add-on pci sound card which worked instantly...  Still bugged by all the unknown devices though.

Hope this helps

---

### Post by jholland on 2008-02-04
I just got a new motherboard with the same chipset on it (7100) and seem to have everything (I need) working.

The video was done by installing Nvidia's binary driver from their website 169, that didn't work initially.  I then performed an 'nvidia-installer --update', which pushed me to version 171, and that worked.

sound was another story.  I followed this guide [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) and everything seems to work (will optical out does).  The only place I deviated was where they talk about looking up the model I just used 'model=auto' and that worked.

---

