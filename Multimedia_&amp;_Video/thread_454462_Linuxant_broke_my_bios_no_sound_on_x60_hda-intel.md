---
title: "Linuxant broke my bios? no sound on x60 hda-intel"
date: 2007-05-25
forum: Multimedia &amp; Video
---

### Post by X-a-v-i on 2007-05-25
Hello all, I intalled Linuxant HSF modem drivers on my ibm x60s. On next reboot sound stop working

reading the forums, I have done lots of changes to my system and nothing. Finally i reinstaled ubuntu and no sound. I tried also to reload bios defaults and nothing... 

I tried also on bios to activate and de-activate the modem and nothing

dmesg when i load the snd_hda_intel module
[ 2541.704000] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[ 2543.596000] ACPI: PCI Interrupt 0000:00:1b.0[B] -> GSI 17 (level, low) -> IRQ 21
[ 2543.596000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[ 2544.024000] hda_codec: invalid dep_range_val 53:1a

Tried also without acpi... nothing

The thing is: **sound worked on fresh feisty installation and after linuxant drivers, i reinstalled feisty and sound doesn't work.**

Should i have to upgrade bios? do i have broken the soundcard? is there any way simply changing IRQs...?

Thanks

---

### Post by roachk71 on 2007-05-25
I wonder if you could post the output from 'lspci -vv' ?

You might have the HCF modem instead. Your best bet is buying an external serial port (hardware) modem...

If your computer has an HSF, though, and installing the Linuxant driver disables sound, uninstalling the driver should restore audio.

Personally I don't trust either the Linuxant drivers or the (as yet unstable) open source one.

---

### Post by X-a-v-i on 2007-05-26
I can't paste the lspci now (i'm in another computer). But what worries me is this: **i reinstalled the full system**, why sound doesn't work like when i installed feisty the first time? what changed? 

-soundcard is broken?
or
-bios changed?

Both installs where with netinstall using billix utility, i suppose in both installations the same packages got installed.

There are lots of problems these days similar than mine on the forums: no sound with lenovo or with hda... and with different soultions or no solution, i read a lot, but i reinstalled Feisty, this is what angry me, it should work loke first time.

In a few hours i wll paste the lspci and all. Thanks

---

### Post by X-a-v-i on 2007-05-26
I tried Feather Linux and i have no audio.
Now i installed Edgy and no audio.
Always the same problem... **can not be kernel related or alsa related, why it doesn't work on other distros? older ditros?**
I'm not sure if the audio missing was because any ubuntu update or the installation of wine and audio testing, or because the linuxant drivers.

I tried all i seen in forums

If someone can help me looking at my logs, i will agree a lot. If there's no solution i will try to update bios (difficult in my laptop)

My lspci:

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Aud
io Controller (rev 02)
        Subsystem: Lenovo Unknown device 2010
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- 
<MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 66
        Region 0: Memory at ee240000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```

my dmesg:

```
[17179594.272000] hda_codec: invalid dep_range_val 53:1a
```

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
```

```
~$ alsamixer
No mixer elems found
```


```
$ ls -l /dev/mixer 
crw-rw---- 1 root audio 14, 0 2007-05-26 20:57 /dev/mixer

$ ls -l /dev/dsp
ls: /dev/dsp: No such file or directory

$ ls -l /dev/audio
ls: /dev/audio: No such file or directory
```


```
$ sudo asoundconf list
Names of available sound cards:
Intel
```

Thanks

---

