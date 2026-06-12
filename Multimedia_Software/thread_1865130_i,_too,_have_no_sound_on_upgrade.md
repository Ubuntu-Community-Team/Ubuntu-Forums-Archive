---
title: "i, too, have no sound on upgrade"
date: 2011-10-19
forum: Multimedia Software
---

### Post by bilmas on 2011-10-19
excited that gnome-shell was finally officially supported i was anxious to upgrade to 11.10.  gnome-shell is still flickering on my system for some reason so i reverted to unity which involved a bit of work since i first started playing around with display drivers

anyway

i know upon initial install i had sound because i watched a youtube video quickly.  since that moment my sound hasn't worked.  typing aplay -l gives me this:

```
david@david:~$ aplay -l
aplay: device_list:240: no soundcards found...
```

but lspci -v will give me this:

```
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at e3400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel modules: snd-hda-intel

```


so i understand it that the system is recognizing the soundcard is there but under sound preferences>hardware there is still nothing listed

any help on this is greatly appreciated!

---

### Post by bilmas on 2011-10-20
i know a lot of people are having this problem but so far can't seem to figure out a solution

anybody getting close?

---

### Post by bilmas on 2011-10-20
hrm...today's update contained some files related to ALSA but still no go

---

### Post by manatlan on 2011-10-22
Same trouble here ;-(

---

### Post by bilmas on 2011-10-23
woof.  let me know if you figure somethingout before i do

---

### Post by theanswriz42 on 2011-10-23
I had sound up until a couple days ago

---

### Post by kommissario on 2011-10-23
try this

go to ubuntu icon at top and select sound in the search field



hardware tag --> select your device

input tag --> select your device

output tag --> select your device

---

### Post by bilmas on 2011-10-24
my device isn't listed i'm afraid

---

### Post by shantiq on 2011-10-24
ok guys experiencing the same but found playing around 2 different ways that it came back on


**1** entering ```
pulseaudio --kill
``` once loaded up

and then pulseaudio --start   [or not] maybe just the first one



**2.** other route is going to systems monitor/processes and terminating pulse


Sometimes it loads up ok for sound but other times not
So maybe try these until the system settles


Those upgrades can be frustrating
Like an equivalent of a cyberbirth :KS
But hey we want the new kiddies even with Unity [yyyyyuuuuuukkk what were they thinking?]

Anyway av a go this way see if it helps some...

---

### Post by bilmas on 2011-10-24
hrm i've tried that before.  unfortunately it doesn't help my computer find my sound card

---

