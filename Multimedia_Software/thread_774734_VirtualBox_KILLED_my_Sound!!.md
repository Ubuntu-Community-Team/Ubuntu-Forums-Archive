---
title: "VirtualBox KILLED my Sound!!"
date: 2008-04-29
forum: Multimedia Software
---

### Post by leech38128 on 2008-04-29
Ok, I needed to have Window$ to do some stuff for school, so I installed Virtualbox (on Hardy x32).  Installation went flawlessly(to those who need to know) except when XP was finished installing and the vm rebooted.  Once it did, it said that it could not find the audio device and would 'turn off' the driver.  I CANNOT duplicate the error! At the time I didn't think anything of it until I wanted to play some music...NO sound.  
Results of 'aplay':
```
leech@stephanie:~$ aplay -l
aplay: device_list:205: no soundcards found...

```
Results of 'lspci -v':
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Dell Unknown device 01d4
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at efebc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

```
I cannot get into the hardware information to find out what driver is being used(none obviously) and when I do this: ```
sudo modprobe snd-
``` and press TAB to flip through the available drivers, nothing happens.
Please advise....please?

---

