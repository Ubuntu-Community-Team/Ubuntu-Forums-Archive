---
title: "maverick &amp; macbook2.1 = no sound"
date: 2010-09-22
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by xxxYURAxxx on 2010-09-22
**lspci:**
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

**dmesg:**
[    9.548901] input: HDA Intel Line In at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    9.549024] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    9.549129] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11

alsamixer master, speaker & speaker0 not 0

but i haven't hear sound at all(speakers & headphones)

can anyone help me?

---

### Post by majortom67 on 2010-09-22
Try pasting the following command:

options snd-hda-intel model=macbook

at the edn of the following file:

alsa-base.conf

(open it: gksudo gedit /etc/modprobe.d/alsa-base.conf

If you don't have such a text string at the end of that file the problem si probably there. The only thing I'm not sure about is if "model=macbook" parameter is OK. I have  a 6,2 MacbookPro and "mbp=55" (Macbook Pro 5,5) is fine but you have a MacBook 2,1 and couldn't find the right string for you (don't think "mb=21" would work...).

---

### Post by linuxopjemac on 2010-09-22
117	ALC882/883/885/888/889
118	======================
125	  macpro	MacPro support
126	  mb5		Macbook 5,1
127	  macmini3	Macmini 3,1
128	  mba21		Macbook Air 2,1
129	  mbp3		Macbook Pro rev3
130	  imac24	iMac 24'' with jack detection
131	  imac91	iMac 9,1
166	  mb31		MacBook 3,1


323	STAC9220/9221
324	=============

328	  intel-mac-v1	Intel Mac Type 1
329	  intel-mac-v2	Intel Mac Type 2
330	  intel-mac-v3	Intel Mac Type 3
331	  intel-mac-v4	Intel Mac Type 4
332	  intel-mac-v5	Intel Mac Type 5
333	  intel-mac-auto Intel Mac (detect type according to subsystem id)
334	  macmini	Intel Mac Mini (equivalent with type 3)
335	  macbook	Intel Mac Book (eq. type 5)
336	  macbook-pro-v1 Intel Mac Book Pro 1st generation (eq. type 3)
337	  macbook-pro	Intel Mac Book Pro 2nd generation (eq. type 3)
338	  imac-intel	Intel iMac (eq. type 2)
339	  imac-intel-20	Intel iMac (newer version) (eq. type 3)


408	Cirrus Logic CS4206/4207
409	========================
410	  mbp55		MacBook Pro 5,5
411	  imac27	IMac 27 Inch

---

### Post by majortom67 on 2010-09-22
Therefore "macbook" should be enough. At least I would try also "mb21" or similars...

---

### Post by xxxYURAxxx on 2010-09-23
i tried each line of them
options snd-hda-intel model=macbook

options snd-hda-intel power_save=10 power_save_controller=N model=intel-mac-v2

and
options snd-hda-intel model=intel-mac-v2

and for each one i tried in sound preferences change profile for analog duplex & digital duplex

but nothing changed and i still can't hear music :(

---

### Post by linuxopjemac on 2010-09-23
are you sure that your channels are unmuted ?

```
alsamixer
```

the ones with mm you have to press  "m" to make them unmuted

---

### Post by xxxYURAxxx on 2010-09-23
of course 
master = 23
Speaker = 100
Speaker 1 = 100
PCM = 100

with options snd-hda-intel model=mb21
every time i boot one of speakers (in gnome-alsamixer) is muted and second one set to 0
and i need to unmute it to get it work

---

### Post by linuxopjemac on 2010-09-23
Set the levels as you want in alsamixer, then:
```
sudo alsactl store
```

Hope that works...

---

### Post by xxxYURAxxx on 2010-09-23
> **linuxopjemac said:**
> Set the levels as you want in alsamixer, then:
```
sudo alsactl store
```

Hope that works...

No it isn't work, after reboot all the levels are default

---

### Post by Elfy on 2010-09-23
moved to maverick forum

---

### Post by moviemaniac on 2010-09-23
try "mbp3" as the model. It's what I have to use with my imac24" and I vaguely remember this also helping a macbook-user I once helped.

If this doesn't help take a look here: [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

### Post by lkjoel on 2010-09-24
> **xxxYURAxxx said:**
> **lspci:**
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

**dmesg:**
[    9.548901] input: HDA Intel Line In at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    9.549024] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    9.549129] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11

alsamixer master, speaker & speaker0 not 0

but i haven't hear sound at all(speakers & headphones)

can anyone help me?
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

