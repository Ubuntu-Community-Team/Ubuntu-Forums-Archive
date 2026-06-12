---
title: "No sound for tv tuner"
date: 2010-03-11
forum: Multimedia Software
---

### Post by xxvirusxx on 2010-03-11
Hello all

After I try to make sound in ubuntu 9.04 but with no luck, I try and 9.10 but the same with no luck. My tv tuner is winfast pvr 2000 xp rm and this tv tuner are using a connector to my motherboard (msi p43 neo-f) in CD-IN. In alsa mixer I haven`t seen CD-IN. Also I edited this **edit /etc/tvtime/tvtime.xml** and replacing **<option name="MixerDevice" value="/dev/mixer:line"/> **whit this one **<option name="MixerDevice" value="/dev/mixer:cd"/> **but I haven`t sound in tv time.

How can enable CD-IN in alsa mixer to have sound on my channels?

Tks

---

### Post by notbad on 2010-05-14
I have the same problem with my Leadtek Winfast TV2000 XP card. at first the Audio Capture device was not loaded. but I figured it out how to enable it. I get video with TV Time but no sound at all. also y tv card is connected to the cd-in plug in the mb. here are some things from terminal:
looks like everything is loaded:
```
tomas@tomas-desktop:~$ dmesg | egrep "bt8|btt"
[   17.307401] bttv: driver version 0.9.18 loaded
[   17.307404] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   17.307749] bttv: Bt8xx card found (0).
[   17.307769] bttv 0000:00:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.307779] bttv0: Bt878 (rev 17) at 0000:00:09.0, irq: 16, latency: 64, mmio: 0xcffff000
[   17.307797] bttv0: detected: Leadtek TV 2000 XP [card=34], PCI subsystem ID is 107d:6609
[   17.307799] bttv0: using: Lifeview FlyVideo 98 LR50 / Chronos Video Shuttle II [card=35,insmod option]
[   17.307802] IRQ 16/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   17.307835] bttv0: gpio: en=00000000, out=00000000 in=003ff502 [init]
[   17.307912] bttv0: FlyVideo_gpio: unknown tuner type.
[   17.307915] bttv0: FlyVideo Radio=no  RemoteControl=no  Tuner=-1 gpio=0x3ff502
[   17.307917] bttv0: FlyVideo  LR90=no  tda9821/tda9820=no  capture_only=no 
[   17.307919] bttv0: tuner type=38
[   17.320997] bttv0: audio absent, no audio device found!
[   17.330218] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   17.341026] bttv0: registered device video0
[   17.341050] bttv0: registered device vbi0
[   17.341066] bttv0: PLL: 28636363 => 35468950 .
[   17.447486] bt87x0: Using board 0, analog, digital (rate 32000 Hz)
[   17.545561] bt878: AUDIO driver version 0.0.0 loaded
tomas@tomas-desktop:~$
```
here I see that the kernel module is not loaded:
```
$ sudo lspci -v
00:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
	Subsystem: LeadTek Research Inc. Device 6609
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at cffff000 (32-bit, prefetchable) [size=4K]
	Capabilities: [44] Vital Product Data <?>
	Capabilities: [4c] Power Management version 2
	Kernel driver in use: bttv
	Kernel modules: bttv

00:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
	Subsystem: LeadTek Research Inc. Device 6609
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at cfffe000 (32-bit, prefetchable) [size=4K]
	Capabilities: [44] Vital Product Data <?>
	Capabilities: [4c] Power Management version 2
	Kernel driver in use: Bt87x

00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
	Subsystem: ABIT Computer Corp. Device 180e
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at f9ff8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```
here's the cards:
```
tomas@tomas-desktop:~$ cat /proc/asound/cards
 0 [SIS966         ]: HDA-Intel - HDA SIS966
                      HDA SIS966 at 0xf9ff8000 irq 18
 1 [Bt878          ]: Bt87x - Brooktree Bt878
                      Brooktree Bt878 at 0xcfffe000, irq 16
```
Also I have made a file to load the modules:
/etc/modprobe.d/bttv.conf with this text:
```
options bttv card=35 tuner=38 (also works with card=34 tuner=43)
options snd_bt87x load_all=1 (without this line my audio ca[ture device is not loaded and is not shown in alsamixer)
```
in /etc/modules I added this:
```
snd_bt87x
bt878
```
here's my alsamixer screen for bt878:
[[IMG]http://img189.imageshack.us/img189/3720/nuotraukat.png[/IMG]](http://img189.imageshack.us/i/nuotraukat.png/)

Is there something I am missing? I tryied this card on windows xp and it works very good and with sound too on the same machine. where is the problem?

---

### Post by notbad on 2010-05-15
so no suggestions?

---

### Post by notbad on 2010-05-15
Aren't here any geeks to solve this problem?:(

---

### Post by lidex on 2010-05-16
Have a look here:
[http://www.linuxtv.org/wiki/index.php/Leadtek_WinFast_2000]("http://www.linuxtv.org/wiki/index.php/Leadtek_WinFast_2000")

---

