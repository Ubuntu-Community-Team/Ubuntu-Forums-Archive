---
title: "Fn+F7 for S-Video/VGA Out Broken?"
date: 2009-11-06
forum: Multimedia Software
---

### Post by moore.bryan on 2009-11-06
Is anyone else experiencing a problem when trying to use Fn+F7 to switch to S-Video/VGA out? My LCD screen goes completely black and nothing show on my projector either.
```

bryan@thinkpad:~$ sudo lshw -C Display
  *-display:0             
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:ee100000-ee17ffff ioport:1800(size=8) memory:d0000000-dfffffff(prefetchable) memory:ee200000-ee23ffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
       resources: memory:ee180000-ee1fffff

```

---

### Post by bovender on 2009-11-06
Yes, I have problems with that too ([here]("http://ubuntuforums.org/showthread.php?t=1315033")).

My screen comes back on again after a second or so, but I don't see anything on the external display.

---

### Post by moore.bryan on 2009-11-06
Well, it sucks to be us, but at least I (and you) are not alone in this. My problem goes a bit further, it would seem, because I *never* get anything back on my LCD and have to hard reboot.

---

### Post by mishkind on 2009-11-10
I have the same problem. Pressing fn f7 makes both outputs go black and I'm forced to eventually press the power button to turn off my computer.
I'm running a thinkpad x60s which uses an intel driver (which from reading around is where I Think the problem is).
All my other Fn keys work fine, and fn+f7 sed to work fine in 9.04.

I found [this]("http://www.thinkwiki.org/wiki/Problem_with_video_output_switching") page on thinkwiki which has some useful tips, but I thought I would check here first before mucking around with all my config files.

If anyone needs any screen dumps to help debug the problem let me know.

---

### Post by moore.bryan on 2009-11-13
I've had good luck with advice from ThinkWiki before; perhaps I'll try this out this weekend and post back with results...

---

### Post by mishkind on 2009-11-17
Any luck?
Thus far this is the only show-stopper I have with 9.10.

---

### Post by moore.bryan on 2009-11-17
Unfortunately, life happened and I wasn't able to "play" this weekend... perhaps this one coming up.

---

### Post by ceasarsk on 2010-02-18
Have the same problem on Ubuntu 9.10 running on Lenovo W500, 
It works when booting into docking-list with external display, but not with laptop screen.

workaround I found is to suspend[Fn+F4]/resume[power on] login and screen is back.
But it's really annoying, anyone know if it's in the new intel driver.

/Ceasar

---

### Post by moore.bryan on 2010-02-19
Sorry for ignoring the thread; all the recent updates to karmic, before I jumped to Lucid testing had fixed my problems. It may be interesting to note, I always used the xorg-edgers ppa on karmic.

---

### Post by mishkind on 2010-12-15
I never managed to get this working with 9.10.
I'm on 10.10 now and everything works out of the box.

---

