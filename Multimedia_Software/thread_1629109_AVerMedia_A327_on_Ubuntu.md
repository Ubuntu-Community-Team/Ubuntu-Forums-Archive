---
title: "AVerMedia A327 on Ubuntu?"
date: 2010-11-23
forum: Multimedia Software
---

### Post by kevin11951 on 2010-11-23
I just got an HP TouchSmart IQ526 as an early Christmas gift, and almost everything is working out of the box.

The only thing that I have found so far that doesn't work, is the TV tuner.  The TV tuner is an AVerMedia A327.

Does anyone know how to get this working?  Google has failed me utterly, and so has searching the forums.

Also, if it matters, I plan to use it as a MythTV box...

---

### Post by Quackers on 2010-11-23
My Avermedie tv card has a Philips semiconductor chip, yours may too and it would be better to Google for that chip number.
Please run ```
lspci
``` in a terminal ( that's a lower case L not a 1 ) and you may see an entry (near the bottom, perhaps) for the device.
If unsure you can post the output here.

---

### Post by kevin11951 on 2010-11-23
> **Quackers said:**
> My Avermedie tv card has a Philips semiconductor chip, yours may too and it would be better to Google for that chip number.
Please run ```
lspci
``` in a terminal ( that's a lower case L not a 1 ) and you may see an entry (near the bottom, perhaps) for the device.
If unsure you can post the output here.

Here you go:

```

 ~ $ sudo lspci -v
**<snip>**
04:00.0 Multimedia video controller: NEC Corporation Device 0165 (rev 0b)
	Subsystem: Avermedia Technologies Inc Device 650a
	Physical Slot: 0-2
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at f9efe000 (64-bit, non-prefetchable) [size=8K]
	Memory at f9efd800 (64-bit, non-prefetchable) [size=2K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number 02-00-4c-00-00-00-00-00
**<snip>**

```

---

### Post by Quackers on 2010-11-23
It's different from mine.
Have you installed tvtime via Synaptic or any other tv program to see if your card is recognised by it?

---

### Post by kevin11951 on 2010-11-23
> **Quackers said:**
> It's different from mine.
Have you installed tvtime via Synaptic or any other tv program to see if your card is recognised by it?

I installed Me-TV, and it says it can't find anything.  I will try tvtime now...  I won't hold my breath ;)

---

### Post by Quackers on 2010-11-23
It's also an option to go and have a mooch around the Multimedia forum and see what the gurus there know :-)

[http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

---

### Post by cariboo on 2010-11-23
You also may want to have a look [here]("http://linuxtv.org/")

---

