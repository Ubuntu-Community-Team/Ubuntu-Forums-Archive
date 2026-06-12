---
title: "Headphones not working on acer aspire 5740G"
date: 2010-04-02
forum: Multimedia Software
---

### Post by popopow on 2010-04-02
Hi,

Just installed an ubuntu 9.10 64 bit on my new Acer Aspire 5740G.

Every thing is working great except that i can't ear anysound on my the heaphones output.

The speakers are working well. But when i go to System > Preferences > Sound > Output and select "Analog Headphones" i get no sound on the headphones.

Here is my alsa info / conf :

**> aaplay -l :**

card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC272 Digital [ALC272 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**> lspci -vv** :

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 033e
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 32
	Region 0: Memory at f0600000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


And finally my **/etc/modprobe.d/alsa-base.conf** :
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N
#
options snd-hda-intel model=auto

I Tried replacing model=auto by model=ALC272 but the problem was still the same.

Any ideas ?

---

### Post by popopow on 2010-04-12
Hi,
A little update with maybe better informations about my config:

[http://www.alsa-project.org/db/?f=32b4c085f9b9d69039b6e3b0af0bc728fe47309e](http://www.alsa-project.org/db/?f=32b4c085f9b9d69039b6e3b0af0bc728fe47309e)

I'm still looking for some help.

---

### Post by popopow on 2010-04-15
Up !
No idea anyone ?

---

### Post by Ulysses361 on 2010-04-15
Try replacing auto with one of the following model options:

Between each reboot, you should only set and test 1 model option at a time.

92	ALC662/663/272
93	==============
94	  3stack-dig	3-stack (2-channel) with SPDIF
95	  3stack-6ch	 3-stack (6-channel)
96	  3stack-6ch-dig 3-stack (6-channel) with SPDIF
97	  6stack-dig	 6-stack with SPDIF
98	  lenovo-101e	 Lenovo laptop
99	  eeepc-p701	ASUS Eeepc P701
100	  eeepc-ep20	ASUS Eeepc EP20
101	  ecs		ECS/Foxconn mobo
102	  m51va		ASUS M51VA
103	  g71v		ASUS G71V
104	  h13		ASUS H13
105	  g50v		ASUS G50V
106	  asus-mode1	ASUS
107	  asus-mode2	ASUS
108	  asus-mode3	ASUS
109	  asus-mode4	ASUS
110	  asus-mode5	ASUS
111	  asus-mode6	ASUS
112	  dell		Dell with ALC272
113	  dell-zm1	Dell ZM1 with ALC272
114	  samsung-nc10	Samsung NC10 mini notebook
115	  auto		auto-config reading BIOS (default)

---

### Post by lidex on 2010-04-15
> **popopow said:**
> Hi,


options snd-hda-intel model=auto

I Tried replacing model=auto by model=ALC272 but the problem was still the same.

Any ideas ?

Try changing to this:
```
options snd-hda-intel model=acer
```
Also go here:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
and install alsa-backports. Reboot after, then check levels in alsamixer.

---

### Post by popopow on 2010-04-16
Thanks, i have already done this. But found the solution by myself. The sound is going out through the spdif outpout. Looks like it acts also as a line out / headphone connector.

---

