---
title: "No sound in Gutsy Gibbon"
date: 2008-10-28
forum: Multimedia Software
---

### Post by sunkssss on 2008-10-28
Hello all,

I was having a real headache trying to get Hardy Heron/Intrepid Ibex installed on my system, so I've gone back to Gutsy Gibbon for reliable performance. So far installation has been a breeze, I've been able to get my wireless adapter working and am working on getting my video drivers configured. However I have not been able to get any sound. I did not have any issues with sound in Hardy or Intrepid, but in Gutsy it's telling my that the volume controller could not find any elements and/or devices to control. It also says that I may not have the right GStreamer plugins installed or that I don't have a sound card configured. 

Could anybody walk me through diagnosing the issue and finding a solution?

Thanks

---

### Post by cyfur01 on 2008-10-28
What kind of sound card do you have? If you don't know, run "lspci | grep -i audio" in a terminal. 

I ran into similar issues with Gutsy and my Hp laptop which uses an Intel 82801H (ICH8 Family) device, and found [this set of solutions]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller").

---

### Post by sunkssss on 2008-10-28
After running that command it came back as...

"00:09.0 Audio device: nVidia Corporation Unknown device 07fc (rev a1)"

---

### Post by cyfur01 on 2008-10-28
There was mention of that message in [this thread.]("http://ubuntuforums.org/showthread.php?t=676032") Seems like it may be a driver issue. (it takes a while after driver development for them to be included in the Linux kernel, and then a bit longer before they work their way into a Ubuntu dist.)

---

### Post by sunkssss on 2008-10-28
So it looks like there may be no hope? I scanned over the thread and there didn't seem to be a solid conclusion. Grr.

---

### Post by Crafty Kisses on 2008-10-28
What are the results of this command?
```
lspci
```

---

### Post by cyfur01 on 2008-10-28
One thing you can attempt to do is, if possible, set up Hardy on another partition, just to see if it can detect what the hardware is (using "lspci", for instance). If it can, then one would at least think you could manually install the drivers on your Gutsy install.

---

### Post by sunkssss on 2008-10-28
> sunkssss@sunkssss-desktop:~$ lspci
00:00.0 Host bridge: nVidia Corporation Unknown device 07c3 (rev a2)
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
00:0f.0 Ethernet controller: nVidia Corporation Unknown device 07dc (rev a2)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)

This was the second time I attempted installing Gutsy on this system, and the first time I had the same issue with my sound.

---

### Post by sunkssss on 2008-10-28
Where could I go about finding out if drivers exist for my system? I can probably crack open some old boxes and find the documentation for my motherboard, so it shouldn't be too hard finding the model name.

---

### Post by sunkssss on 2008-10-28
This is a non-issue for me now, since I've figured out a way to get Hardy working smoothly on my system with sound intact. Thanks though.

---

