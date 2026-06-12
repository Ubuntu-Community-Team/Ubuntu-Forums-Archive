---
title: "Upgrade to intrepid did break sound"
date: 2009-02-28
forum: Multimedia Software
---

### Post by pieroxy on 2009-02-28
I had sound with no issue before upgrading to Intrepid....

Now I have no sound anymore and here is what happens:

```
aplay -l
aplay: device_list:215: no soundcards found...
```


My mobo is a A7N8X-XE from ASUS and the sound card is:

```
lspci -v
(...)
00:06.0 Multimedia audio controller: nVidia Corporation MCP2S AC'97 Audio Controller (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 8198
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
	I/O ports at d800 [size=256]
	I/O ports at e000 [size=128]
	Memory at ff6ff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
(...)

```

Typing "sudo modprobe snd-" and TAB did not get me anywhere as it is not displaying anything (that's what the tuto advises to do). 

Can anyone help? There must be something simple as it worked well just before the upgrade!

---

### Post by pieroxy on 2009-03-07
I also tried the following:

```
sudo aptitude install linux-ubuntu-modules-`uname -r` linux-generic
```

It did install some modules but even after rebooting, no luck, no sound and aplay -l still cannot find any soundcard

---

### Post by pieroxy on 2009-03-16
I'm out of ideas on that one. I've tried every HOWTO I've found with no luck...

Does anyone has the slightlest idea?

---

