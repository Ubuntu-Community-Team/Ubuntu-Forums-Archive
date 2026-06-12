---
title: "No sound; card not supported?"
date: 2011-08-08
forum: Multimedia Software
---

### Post by sks24 on 2011-08-08
Machine: Presario CQ57  64 bit  10.04.3 LTS

```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
lspci -v [...] 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
	Subsystem: Hewlett-Packard Company Device 3577
	Flags: bus master, slow devsel, latency 32, IRQ 16
	Memory at 90440000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

So it looks like all the drivers for ATI devices are [here]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-ATI"), and it looks like I would be working from [these instructions]("http://www.alsa-project.org/main/index.php/Matrix:Module-usb-audio"), no?

It's not clear to me whether my card is supported.  I'm willing to try all this - working in a shell and so forth - as long as . . . there's a reasonable chance for a pot 'o gold at the end.

I'm not a coder.  Might need a bit of hand holding.  

Thanks in advance,
Scott

---

### Post by sks24 on 2011-08-09
So, 
1) is this card supported?  If you don't know for sure, that's fine, because,
2) I'm thinking that I'll just come back to this machine in a few months and try both the LTS and the latest distro - 11.10, no? - in both the dedicated Linux partition and the VirtualBox on the Win7 side of this machine.  (I can't get anything to install in the VirtualBox. See: [http://ubuntuforums.org/showthread.php?t=1819171](http://ubuntuforums.org/showthread.php?t=1819171)

And "2)" because it's reasonable to suppose there will be code present such that the (say, 11.10) Ubuntu installation will fully support all the devices on this machine "out of the box"?  

Thanks in advance,
Scott

---

### Post by .... on 2011-08-09
The chip is supported, but you may need to upgrade to latest ALSA: [U][http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)
[/U]Actually, the first thing to do is check alsamixer and make sure nothing's muted:
```
alsamixer
```

---

### Post by sks24 on 2011-08-09
Thanks ....

So I attached a screenshot of the mixer; doesn't look like anything is muted.  The sound card selected is "default."

How might I determine if I need the upgrade?  Or should I just download the script and try to install it and see what kind of noises it makes?  

It looks like I would download the script [here]("http://www.alsa-project.org/main/index.php/Download").  Do I download all the 1.0.24 stable releases on that page? (Drivers, firmware, and so forth)



Thanks,
Scott

---

### Post by sks24 on 2011-08-11
This is not that big of a deal.  I'll revisit this machine a couple of weeks (at least) after 11.10 is released, and install that distro and see how it does.  I'll leave this open just in case someone comes up with a couple of quick terminal commands which would (likely) fix this.

Thanks,
Scott

---

### Post by .... on 2011-08-11
Easy ALSA upgrade script: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

---

### Post by sks24 on 2011-08-11
It's the one labeled "AlsaUpgrade-1.0.24-2.tar.gz (6.7 KB, 3402 views)," under where he talks about "Possible future improvements to the script if/when I'm feeling more motivated," no?

---

### Post by .... on 2011-08-11
> **sks24 said:**
> It's the one labeled "AlsaUpgrade-1.0.24-2.tar.gz (6.7 KB, 3402 views)," under where he talks about "Possible future improvements to the script if/when I'm feeling more motivated," no?
Correct.

---

### Post by drs305 on 2011-08-11
> **albert56 said:**
> can someone help me configure desktop speakers with windows xp

Albert,

Welcome to the Ubuntu Forums. Unfortunately this is a Ubuntu/Linux support forum and not one for Windows. While we deal with Windows issues from time to time, especially for dual boot problems, a specific support request for another OS is not the purpose of this forum.

At this point, if I was a Windows user, I would gladly provide some links to good Windows forums that should be able to help you with your problem. If another user wishes to provide those links that's ok, but otherwise we will just have to wish you well in your quest for a solution.

---

### Post by sks24 on 2011-08-11
Thank you very much for your help Mister Four Dots.  
Best!
SKS

---

### Post by .... on 2011-08-11
So.... do you have sound?

---

### Post by sks24 on 2011-08-11
No.  But I haven't tried the script yet, either.  After I do so, I'll come back with a report and/or "solved."  Probably within the week.  

Again, thanks for your help.

---

