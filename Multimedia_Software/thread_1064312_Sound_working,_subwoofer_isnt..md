---
title: "Sound working, subwoofer isnt."
date: 2009-02-08
forum: Multimedia Software
---

### Post by Sinmok on 2009-02-08
Hey all. I recently switched to Ubuntu from vista. Everything is working fine, except my subwoofer. Sound plays from my speakers just fine.

My subwoofer and speakers are built in directly to my laptop (Toshiba Qosmio F50)

According to the terminal I have:

```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f2400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

I have alsa mixer selected too. Any and all help is appreciated.

---

### Post by Sinmok on 2009-02-09
bump

---

### Post by kostkon on 2009-02-09
OK, it seems that your woofer has its own channel, so you have a 2.1 configuration.

But, what version of Ubuntu do you have?

---

### Post by Sinmok on 2009-02-09
I'm using the up to date ubuntu, 8.10

---

### Post by kostkon on 2009-02-09
OK. Then, you need to follow [this guide]("http://ubuntuforums.org/showthread.php?t=795525") to enable surround sound in *PulseAudio*. Follow the way that applies to your case.

Hope that helps.

---

### Post by Sinmok on 2009-02-09
Wow, worked perfectly. Unfortunately, the sound quality isn't as good as windows, but I can't complain. Thank you!

---

### Post by abdusamed on 2009-08-20
I have the same problem.. i have ubuntu 9.04 and my f50 subwoofer not working. I also dont know how to get the audi info which the first post has on my terminal..thanks

---

### Post by abdusamed on 2010-08-17
According to the thread, I simple had to select the device from 'Sound Preferences' and select 'Surround' but I don't have any option to select that! It's only stereo! Do I need to install something else? I'm on lucid

---

### Post by abdusamed on 2010-08-17
~bump

---

### Post by lidex on 2010-08-17
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by abdusamed on 2010-08-21
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

Laptop Model

[list]
**Qosmio F50 -126**
[/list]

--Detail specs : [Click Here](http://eu.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=EU&com.broadvision.session.new=Yes&PRODUCT_ID=1061504)

Result after running the commands you mentioned:-

```

bahie@bahie-laptop:~$ uname -a
Linux bahie-laptop 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64 GNU/Linux
bahie@bahie-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC272 Digital [ALC272 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
bahie@bahie-laptop:~$ dpkg -l | grep "alsa"
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA
ii  libsox-fmt-alsa                       14.3.0-1.1build1                                SoX alsa format I/O library
bahie@bahie-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC272

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040

==> /proc/asound/card0/codec#3 <==
Codec: Nvidia MCP78 HDMI
bahie@bahie-laptop:~$ 

```

---

### Post by abdusamed on 2010-08-23
bump

---

### Post by lidex on 2010-08-23
Try this and see if you gain any profiles. 
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=auto 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by abdusamed on 2010-08-24
Did that and I am able to select HDA Intel but it doesn't do anything particular.... sub woofer still doesn't work

---

### Post by lidex on 2010-08-25
> **abdusamed said:**
> Did that and I am able to select HDA Intel but it doesn't do anything particular.... sub woofer still doesn't work

HDA Intel would be your soundcard. On the sound preferences hardware tab, do you have a profile for 2.1?

---

### Post by abdusamed on 2010-08-25
> **lidex said:**
> HDA Intel would be your soundcard. On the sound preferences hardware tab, do you have a profile for 2.1?

I didn't find anything which read 2.1. All the numbers and names are the same as they were when before I did the gksudo gedit file.

Here's the screenshot of the sound hardware tab


[IMG]http://img261.imageshack.us/img261/6651/soundpreferences019.png[/IMG]

---

### Post by lidex on 2010-08-25
Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by abdusamed on 2010-08-25
> **lidex said:**
> Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```Reference the Ubuntu-Bug Audio link in my sig.

Don't know if this might help u but I noticed the terminal now shows an extra device which doesn't seem to be activated.

Running the commands you earlier posted;


[list]
bahie@bahie-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
[COLOR=Red][B]card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0[/B][/COLOR]
card 0: Intel [HDA Intel], device 1: ALC272 Digital [ALC272 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/list]


```

bahie@bahie-laptop:~$ uname -a
Linux bahie-laptop 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:38:40 UTC 2010 x86_64 GNU/Linux
bahie@bahie-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC272 Digital [ALC272 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
bahie@bahie-laptop:~$ dpkg -l | grep "alsa"
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA
ii  libsox-fmt-alsa                       14.3.0-1.1build1                                SoX alsa format I/O library
bahie@bahie-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC272

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040

==> /proc/asound/card0/codec#3 <==
Codec: Nvidia MCP78 HDMI

```

---

### Post by abdusamed on 2010-09-03
bump!

---

### Post by abdusamed on 2010-09-05
bump...

---

### Post by lidex on 2010-09-05
> **abdusamed said:**
> bump...

You really should rule out a hardware issue. Doesn't your sub not work in windows as well? Maybe try some different distros

---

### Post by abdusamed on 2010-09-10
> **lidex said:**
> You really should rule out a hardware issue. Doesn't your sub not work in windows as well? Maybe try some different distros


It is working fine in windows seven with sound quality being much much better than ubuntu. Note I did not install any third party drivers on it, simple windows install, update, working :).... 


the same story doesn't go with ubuntu

---

### Post by abdusamed on 2010-10-16
But didn't you notice the message? it now detects it but doesn't seem to enable it...

---

### Post by lidex on 2010-10-17
Back to post #16. The profile dropdown menu at the bottom of the hardware tab. Can you post a screen of the options that appear when you click on it?

---

### Post by abdusamed on 2010-10-18
> **lidex said:**
> Back to post #16. The profile dropdown menu at the bottom of the hardware tab. Can you post a screen of the options that appear when you click on it?

Sorry not yet, I'm short in time.. Shutter doesn't seem to see the menu opened, print screen doesn't work when the menu is opened...

---

### Post by abdusamed on 2010-10-30
> **lidex said:**
> Back to post #16. The profile dropdown menu at the bottom of the hardware tab. Can you post a screen of the options that appear when you click on it?

```

Off
Analog Stereo Input
Digital Stereo [HDMI] Output
Digital Stereo [HDMI] Output + Analog Stereo Input
Digital Stereo Duplex [IEC958]
Digital Stereo Duplex [IEC958] + Analog Stereo Input
Analog Stereo Output
Analog Stereo Duplex -> The one selected currently

```

...On the side note, neither shutter nor simple print screen were picking up the menu to screen shot! Print screen won't do anything while Shutter won't capture anything.

---

### Post by abdusamed on 2010-11-08
Bump!~

---

### Post by abdusamed on 2010-11-10
bump_

---

### Post by abdusamed on 2010-11-13
bump

---

### Post by abdusamed on 2011-02-02
bump

the sound in seven is better than ubuntu... trust me it really is


But i don't exactly know why? I have dobly something installed in seven..anything related to it on ubuntu?

---

### Post by lidex on 2011-02-02
Have you tried maverick?

---

### Post by abdusamed on 2011-02-25
> **lidex said:**
> Have you tried maverick?


No I haven't. I recently updated my machine to Ubuntu 10.04.2. Guess what? No change. I don't understand what I'm missing. Tried on windows and believe me, the sound quality is amazing, my notebooks vibrates the table! 

I don't understand why formating and runng maverick will make any what so ever difference.

---

### Post by lidex on 2011-03-01
> **abdusamed said:**
> No I haven't. I recently updated my machine to Ubuntu 10.04.2. Guess what? No change. I don't understand what I'm missing. Tried on windows and believe me, the sound quality is amazing, my notebooks vibrates the table! 

[COLOR="Red"]I don't understand why formating and runng maverick will make any what so ever difference.[/COLOR]

No need to format anything. You can install to a different partition side-by-side or simply try the LiveCD or install and boot into a newer kernel in Lucid:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

---

### Post by abdusamed on 2011-03-05
> **lidex said:**
> No need to format anything. You can install to a different partition side-by-side or simply try the LiveCD or install and boot into a newer kernel in Lucid:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

Sorry for replying so late but I did install the new kernel - the lastest one supported by lucid. There was no sound quality difference whats so ever other than nividia driver messing up. Back to the stock kernel. 

The kernel didn't make the sound work which I can safely assume nothing was done. 

Should I try something else now????

---

### Post by lidex on 2011-03-06
Try booting into maverick live-session. 
[http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)

---

### Post by abdusamed on 2011-03-07
I will try that soon but it will take a while. But I thought why not simply boot into Natty??? 

Another thing, what makes you sure or even have the thought of it working on the newer version? I haven't seen anything 'built' support the subwoofer or improving the sound quality.

---

### Post by edup_pt on 2011-12-05
HI,

Did you find a solution for this post?

Many Thanks.

I already spent days on this.



 I have an HP ENVY 14 2020ep Notebook beats audio edition:
 Intel® Core™ i7-2630QM Quad Core (Sandy Bridge)
8 GB
Version
 IT brings a special sound card (beats system).
 Im not taking all the possibilities of this system. I have the basic  configuration for it. Ubuntu 11.10 does not recognize the hardware as it  is.
 In sound output i only have:
 Internal Audio Analog Stereo hardware
 I using only 2 speakers (Analog Stereo Duplex) and im not using even the subwoofer.
 I followed this forum (and others) to solve the situation, but no solution.




Hardware:
 

edup@beatsaudio:~$ uname -a
Linux beatsaudio 3.0.0-13-generic-pae #22-Ubuntu SMP Wed Nov 2 15:17:35 UTC 2011 i686 i686 i386 GNU/Linux
 

edup@beatsaudio:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
 edup@beatsaudio:~$ dpkg -l | grep "alsa"
ii  alsa-base                                1.0.24+dfsg-0ubuntu2                       ALSA driver configuration files
ii  alsa-utils                               1.0.24.2-0ubuntu8.1                        Utilities for configuring and using ALSA
rc  alsamixergui                             0.9.0rc2-1-9                                graphical soundcard mixer for ALSA soundcard driver
ii  bluez-alsa                               4.96-0ubuntu4                              Bluetooth ALSA support
rc  gnome-alsamixer                          0.9.7~cvs.20060916.ds.1-2ubuntu1           ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                       0.10.35-1                                  GStreamer plugin for ALSA
 



edup@beatsaudio:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD81B1X5
 ==> /proc/asound/card0/codec#3 <==
Codec: Intel CougarPoint HDMI
 ProblemType: Bug
DistroRelease: Ubuntu 11.10
Package: alsa-base 1.0.24+dfsg-0ubuntu2
ProcVersionSignature: Ubuntu 3.0.0-13.22-generic-pae 3.0.6
Uname: Linux 3.0.0-13-generic-pae i686
NonfreeKernelModules: fglrx
AlsaVersion: Advanced Linux Sound Architecture Driver Version 1.0.24.
ApportVersion: 1.23-0ubuntu4
Architecture: i386
ArecordDevices:
 **** List of CAPTURE Hardware Devices ****
 card 0: PCH [HDA Intel PCH], device 0: STAC92xx Analog [STAC92xx Analog]
   Subdevices: 1/1
   Subdevice #0: subdevice #0
AudioDevicesInUse:
 USER        PID ACCESS COMMAND
 /dev/snd/controlC0:  edup       1867 F.... pulseaudio
Card0.Amixer.info:
 Card hw:0 'PCH'/'HDA Intel PCH at 0xc9700000 irq 54'
   Mixer name	: 'Intel CougarPoint HDMI'
   Components	: 'HDA:111d7605,103c3385,00100105 HDA:80862805,80860101,00100000'
   Controls      : 22
   Simple ctrls  : 11
Date: Mon Dec  5 13:01:37 2011
InstallationMedia: Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
PackageArchitecture: all
ProcEnviron:
 PATH=(custom, no user)
 LANG=en_US.UTF-8
 SHELL=/bin/bash
SourcePackage: alsa-driver
Symptom: audio
Symptom_AlsaPlaybackTest: ALSA playback test through plughw:PCH successful
Symptom_Card: Internal Audio - HDA Intel PCH
Symptom_Jack: Speaker, Internal
Symptom_PulsePlaybackTest: PulseAudio playback test successful
Symptom_Type: None of the above
Title: [HP ENVY 14 Notebook PC, IDT 92HD81B1X5, Speaker, Internal] Playback problem
UpgradeStatus: Upgraded to oneiric on 2011-11-19 (16 days ago)
dmi.bios.date: 05/30/2011
dmi.bios.vendor: Hewlett-Packard
dmi.bios.version: F.04
dmi.board.asset.tag: Base Board Asset Tag
dmi.board.name: 3385
dmi.board.vendor: Hewlett-Packard
dmi.board.version: KBC Version 93.0F
dmi.chassis.asset.tag: CNU12824NX
dmi.chassis.type: 10
dmi.chassis.vendor: Hewlett-Packard
dmi.chassis.version: Chassis Version
dmi.modalias: dmi:bvnHewlett-Packard:bvrF.04:bd05/30/2011:svnHewlett-Packard:pnHPENVY14NotebookPC:pvr0586200000241A10001620100:rvnHewlett-Packard:rn3385:rvrKBCVersion93.0F:cvnHewlett-Packard:ct10:cvrChassisVersion:
dmi.product.name: HP ENVY 14 Notebook PC
dmi.product.version: 0586200000241A10001620100
dmi.sys.vendor: Hewlett-Packard
mtime.conffile..etc.modprobe.d.alsa.base.conf: 2011-12-05T12:50:57.168500

---

### Post by lidex on 2011-12-27
Any luck?
Try the alsa-info script. It provides some valuable info.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by __lonewolf on 2012-01-13
I am seeing the same issue.  Here is the link to the alsa info.  Alsamixer, pavucontrol only show 2 channels.

[http://www.alsa-project.org/db/?f=a8b1fe3d3e9e457f9fef6b3583e77b41aea5ea29](http://www.alsa-project.org/db/?f=a8b1fe3d3e9e457f9fef6b3583e77b41aea5ea29)

HP DV6-6145dx running 11.10.  

00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h Processor Root Complex [1022:1705]
	Subsystem: Advanced Micro Devices [AMD] Family 12h Processor Root Complex [1022:1705]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32

00:01.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:9641] (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device [103c:358b]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 53
	Region 0: Memory at e0000000 (32-bit, prefetchable) [size=256M]
	Region 1: I/O ports at 3000 [size=256]
	Region 2: Memory at f0300000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

00:01.1 Audio device [0403]: ATI Technologies Inc Device [1002:1714]
	Subsystem: Hewlett-Packard Company Device [103c:358b]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 52
	Region 0: Memory at f0344000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Family 12h Processor Root Port [1022:1709] (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Family 12h Processor Root Port [1022:170a] (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: f0200000-f02fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Family 12h Processor Root Port [1022:170b] (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: f0100000-f01fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:10.0 USB Controller [0c03]: Advanced Micro Devices [AMD] Hudson USB XHCI Controller [1022:7812] (rev 03) (prog-if 30 [XHCI])
	Subsystem: Hewlett-Packard Company Device [103c:358b]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at f0348000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci-hcd

00:10.1 USB Controller [0c03]: Advanced Micro Devices [AMD] Hudson USB XHCI Controller [1022:7812] (rev 03) (prog-if 30 [XHCI])
	Subsystem: Hewlett-Packard Company Device [103c:358b]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at f034a000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci-hcd

00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode] [1022:7804] (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Device [103c:358b]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 51
	Region 0: I/O ports at 3138 [size=8]
	Region 1: I/O ports at 314c [size=4]
	Region 2: I/O ports at 3130 [size=8]
	Region 3: I/O ports at 3148 [size=4]
	Region 4: I/O ports at 3110 [size=16]
	Region 5: Memory at f0350000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:12.0 USB Controller [0c03]: Advanced Micro Devices [AMD] Hudson USB OHCI Controller [1022:7807] (rev 11) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device [103c:358b]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at f034f000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller [0c03]: Advanced Micro Devices [AMD] Hudson USB EHCI Controller [1022:7808] (rev 11) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device [103c:358b]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at f034e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller [0c03]: Advanced Micro Devices [AMD] Hudson USB OHCI Controller [1022:7807] (rev 11) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device [103c:358b]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at f034d000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller [0c03]: Advanced Micro Devices [AMD] Hudson USB EHCI Controller [1022:7808] (rev 11) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device [103c:358b]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at f034c000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] Hudson SMBus Controller [1022:780b] (rev 13)
	Subsystem: Hewlett-Packard Company Device [103c:358b]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface [0101]: Advanced Micro Devices [AMD] Hudson IDE Controller [1022:780c] (rev 40) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Hewlett-Packard Company Device [103c:358b]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: I/O ports at 3128 [size=8]
	Region 1: I/O ports at 3144 [size=4]
	Region 2: I/O ports at 3120 [size=8]
	Region 3: I/O ports at 3140 [size=4]
	Region 4: I/O ports at 3100 [size=16]
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp

00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] Hudson Azalia Controller [1022:780d] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:358b]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f0340000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] Hudson LPC Bridge [1022:780e] (rev 11)
	Subsystem: Hewlett-Packard Company Device [103c:358b]
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] Hudson PCI Bridge [1022:780f] (rev 40) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=64
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 [1022:1700] (rev 43)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1 [1022:1701]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2 [1022:1702]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3 [1022:1703]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: <access denied>
	Kernel driver in use: k10temp
	Kernel modules: k10temp

00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4 [1022:1704]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.5 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6 [1022:1718]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.6 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5 [1022:1716]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.7 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7 [1022:1719]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Hewlett-Packard Company Device [103c:358b]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 40
	Region 0: I/O ports at 2000 [size=256]
	Region 2: Memory at f0004000 (64-bit, prefetchable) [size=4K]
	Region 4: Memory at f0000000 (64-bit, prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

02:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
	Subsystem: Hewlett-Packard Company Device [103c:1636]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at f0200000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: rt2800pci
	Kernel modules: rt2800pci

03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader [10ec:5209] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:358b]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at f0100000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: rts_pstor
	Kernel modules: rts_pstor

default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
hdmi:CARD=Generic,DEV=0
    HD-Audio Generic, HDMI 0
    HDMI Audio Output
dmix:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample mixing device
dsnoop:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample snooping device
hw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Hardware device with all software conversions
front:CARD=Generic_1,DEV=0
    HD-Audio Generic, STAC92xx Analog
    Front speakers
surround40:CARD=Generic_1,DEV=0
    HD-Audio Generic, STAC92xx Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Generic_1,DEV=0
    HD-Audio Generic, STAC92xx Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Generic_1,DEV=0
    HD-Audio Generic, STAC92xx Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Generic_1,DEV=0
    HD-Audio Generic, STAC92xx Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Generic_1,DEV=0
    HD-Audio Generic, STAC92xx Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=Generic_1,DEV=0
    HD-Audio Generic, STAC92xx Analog
    Direct sample mixing device
dsnoop:CARD=Generic_1,DEV=0
    HD-Audio Generic, STAC92xx Analog
    Direct sample snooping device
hw:CARD=Generic_1,DEV=0
    HD-Audio Generic, STAC92xx Analog
    Direct hardware device without any conversions
plughw:CARD=Generic_1,DEV=0
    HD-Audio Generic, STAC92xx Analog
    Hardware device with all software conversions



thanks!

---

### Post by m7esain on 2012-06-13
hello, all
im having the same problem with my HP DV6-6145dx

and donno howto fix it

can anyone explain the instruction??

---

### Post by edup_pt on 2012-06-14
Please follow this bug post:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/900278](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/900278)

---

### Post by edup_pt on 2012-06-14
Please follow this post:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/900278](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/900278)

---

### Post by m7esain on 2012-06-18
@[edup_pt]("http://ubuntuforums.org/member.php?u=921876")
buddy , i didn't understand any thing 

Can you explain how to fix this issue in a simple way?

---

