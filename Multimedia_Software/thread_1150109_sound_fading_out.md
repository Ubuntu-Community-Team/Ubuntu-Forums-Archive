---
title: "sound fading out"
date: 2009-05-05
forum: Multimedia Software
---

### Post by helmet on 2009-05-05
I've have this problem which Google tells me other people have experienced but I have yet to find a solution.

I can fiddle around enough to get the audio test in the Sound dialog producing noise, but it just fades out.....gradually, until there is no sound at all. What gives?

Dell E521, Jaunty 32bit, nvidia hda intel.

I've tried the model=[dell-]3stack stuff but it doesn't work. Fresh install.

---

### Post by Lachinchon on 2009-06-04
I just installed jaunty on a Dell (DM061) for my partner (who thought the rapture had come when he was no longer chained to Bill Gates).  However, he says he is having the same audio issue, i.e. fading of sound until no sound.  Sound is fine at boot and will be ok for awhile before the problem manifests itself.  I can find no obvious hardware or software defect.  I see that there have been no replies to this original post for 4 weeks, so perhaps this is an isolated issue or one with no solution. Any insight would be appreciated.

...and keep in mind: There are some things it is impossible to know, but it is impossible to know these things.

---

### Post by mantelo on 2009-06-30
I'm having the same problem (dell E521, Jaunty fresh install), but it seems to being triggered when I connect my headphones in the front jack.

The sound would work fine for hours, but if I hook up to the front audio jack, starts to fade until it dies.

---

### Post by The Big Chow Mein on 2009-09-09
I have the exact same problem with an E521 and jaunty, any help would be much appreciated. 

Just to note its as above the sound only fades if i plug in headphones into the front panel.

---

### Post by jefferystone on 2009-10-30
Guys,

I had the same issue with jaunty and karmic causing fading when the headphones are plugged in.

You could try the following without rebooting to get the sound back:

killall pulseaudio
sudo alsa force-reload
pulseaudio --start -D

For a permanent fix, you can edit /etc/modprobe.d/alsa-base.conf to have the following:

for Jaunty:  options snd-hda-intel model=ref

for Karmic:  options snd-hda-intel power_save=10 power_save_controller=N model=ref

You could substitute model=3stack, but for me it didn't provide all of the possibilities.  I tried the follow "models=" options, but they still allowed the fading to occur:  dell-3stack, 5stack, 6stack, dell-bios

You really should reboot after making the change to /etc/modprobe.d/alsa-base.conf.

For Karmic, the only hardware that produces consistent sound are "Analog Stereo Duplex" and "Analog Stereo Output" even though I have 4.1 speakers.

Maybe this will be fixed later.

Let me know if this worked for you.

Sincerely,

Jeffery Stone

---

### Post by lfaraone on 2009-11-15
The bug for this is at [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/279478](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/279478) , and it should already be fixed in Lucid.

---

### Post by MrQuincle on 2009-11-16
On my system (Ubuntu Karmic Koala, 9.10) I had to add the 5stack model to /etc/modprobe.d/alsa-base.conf:

```

# Power down HDA controllers after 10 idle seconds
# Added also model=5stack
options snd-hda-intel power_save=10 power_save_controller=N model=5stack
```

Check also this excellent guide: [SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

For your convenience I will add additional information about my system. Perhaps it might help someone who encounters the same problem that his/her sound fades away in say 20 seconds.

```

uname -a
Linux deix 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
```

```

< /var/log/syslog grep audio
Nov 16 09:17:25 localhost pulseaudio[2773]: module-x11-xsmp.c: X11 session manager not running.
Nov 16 09:17:25 localhost pulseaudio[2773]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Nov 16 10:17:47 localhost pulseaudio[2773]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Nov 16 10:17:47 localhost pulseaudio[2773]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Nov 16 10:17:47 localhost pulseaudio[2773]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Nov 16 13:35:11 localhost pulseaudio[13585]: pid.c: Daemon already running.
Nov 16 13:43:10 localhost pulseaudio[14498]: ratelimit.c: 160 events suppressed
```

```

lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

Use this information to retrieve more:
```

sudo lspci -vv -s 00:1b.0
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Device 01dd
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at dffdc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [70] Express (v1) Root Complex Integrated Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
			ClockPM- Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

```

sudo lshw -c multimedia
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:16 memory:dffdc000-dffdffff
```

---

