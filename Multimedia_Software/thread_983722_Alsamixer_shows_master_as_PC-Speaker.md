---
title: "Alsamixer shows master as PC-Speaker"
date: 2008-11-16
forum: Multimedia Software
---

### Post by lyznx on 2008-11-16
Cliffs: sound coming from pc-speaker, not my desktop speakers. See below for details. 

I have been trying to figure out what is going on here for a couple of days now.
 It all started when I tried to install a prorietary video driver (Nvidia).
 My sound just hasnt been right since. I dont think that the driver even installed. It never even finished I think. And I never tryed to finish once things went bad.

 Anywho, That way the root of the problem before you might ask what it was I was doing to mess it up.

Now, I have been going over this page, [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) many times.
 I have done the steps many times. And it gets better each time. but yesterday when I turned on my computer, The sound no longer came from my desktop speaker. It comes from inside the pc (scratching).
 When I go into the terminal and type alsamixer, it says,
 card: pcsp
 Chip: pc-speaker etc.

 This is the problem right?
 Can somebody tell me who to change this?
 Thank you much.

---

### Post by psyke83 on 2008-11-16
> **lyznx said:**
> Cliffs: sound coming from pc-speaker, not my desktop speakers. See below for details. 

I have been trying to figure out what is going on here for a couple of days now.
 It all started when I tried to install a prorietary video driver (Nvidia).
 My sound just hasnt been right since. I dont think that the driver even installed. It never even finished I think. And I never tryed to finish once things went bad.

 Anywho, That way the root of the problem before you might ask what it was I was doing to mess it up.

Now, I have been going over this page, [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) many times.
 I have done the steps many times. And it gets better each time. but yesterday when I turned on my computer, The sound no longer came from my desktop speaker. It comes from inside the pc (scratching).
 When I go into the terminal and type alsamixer, it says,
 card: pcsp
 Chip: pc-speaker etc.

 This is the problem right?
 Can somebody tell me who to change this?
 Thank you much.

What version of Ubuntu are you running? This bug existed during the Intrepid development cycle, but it was fixed before release.

Please paste the contents of /etc/modprobe.d/alsa-base, and the output of:
```
$ aplay -l
```

---

### Post by lyznx on 2008-11-16
In another sense, I need to change my default audio device from my PC_SPEAKER to my INTEL 
 I have gone through the sound menu under preference    IT DOESNT WORK.

---

### Post by lyznx on 2008-11-16
> **psyke83 said:**
> What version of Ubuntu are you running? This bug existed during the Intrepid development cycle, but it was fixed before release.

Please paste the contents of /etc/modprobe.d/alsa-base, and the output of:
```
$ aplay -l
```

Thank you for your help.

bash: $: command not found
c4@c4-desktop:~$  aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: pcsp [pcsp], device 0: pcspeaker [pcsp]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by psyke83 on 2008-11-16
> **lyznx said:**
> Thank you for your help.

bash: $: command not found
c4@c4-desktop:~$  aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: pcsp [pcsp], device 0: pcspeaker [pcsp]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Your real sound card is detected, but at the wrong index. Please paste the contents of the alsa-base file I mentioned, and let me know your version of Ubuntu.

---

### Post by lyznx on 2008-11-16
> **psyke83 said:**
> Your real sound card is detected, but at the wrong index. Please paste the contents of the alsa-base file I mentioned, and let me know your version of Ubuntu.

8.04 hardy

autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388#

---

### Post by psyke83 on 2008-11-16
Append the following text to the bottom of /etc/modprobe.d/alsa-base, then save:
```

# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
```

Your real sound card should be chosen as the default after a reboot.

---

### Post by lyznx on 2008-11-16
> **psyke83 said:**
> Append the following text to the bottom of /etc/modprobe.d/alsa-base, then save:
```

# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
```

Your real sound card should be chosen as the default after a reboot.

Im gonna try this out.  Brb.
 Thanks again...

---

### Post by lyznx on 2008-11-16
It says I dont have permission to save the file. 
 I have full control. Is there something I need to unlock?
 I think I need to be root. Do I need to leave the system for that? And does root have a default pass, as I have never logged in as root before?

 Sorry such a noob.

---

### Post by psyke83 on 2008-11-16
> **lyznx said:**
> It says I dont have permission to save the file. 
 I have full control. Is there something I need to unlock?
 I think I need to be root. Do I need to leave the system for that? And does root have a default pass, as I have never logged in as root before?

 Sorry such a noob.

Edit the file as superuser, i.e.:

```
$ gksudo gedit /etc/modprobe.d/alsa-base
```

---

### Post by lyznx on 2008-11-16
> **psyke83 said:**
> Edit the file as superuser, i.e.:

```
$ gksudo gedit /etc/modprobe.d/alsa-base
```

Your The Man!!!
 It worked.
 Thank you a thousand times!

---

### Post by lyznx on 2008-11-16
OK. Im worst off now than when I started.
 Here is the deal.
 The speakers were working perfectly.
 I went to bed (leaving the computer on), woke up, and viola NO SOUND.
 I decided to restart, and now The sound shows up in the system tray as muted.
 alsamixer no longer works. It reads, "alsamixer: function snd_ctl_open failed for default: No such device"
 When I double click on the sound in the speaker tray, it says "No volume control gstreamerplugins and/or devices found."
 I looked through this thread, [http://ubuntuforums.org/showthread.php?t=543793](http://ubuntuforums.org/showthread.php?t=543793) and reinstalled/installed all those apps in synaptic.
 I tried booting into different kernels.
 I even went back to [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and tried these steps again.
 What the hell. This is so freaking annoying.
 Somebody please help me out. Im about to go postal.
I even booted up into the Ubuntu cd, hoping there was a repair feature on there. Another 45 minutes wasted on waiting for that to load and unload.
 I spend more time trying to fix things and google things on Ubuntu than actually getting use out of it.
 I have been working on this thing since 6am this morning.

---

### Post by lyznx on 2008-11-16
c4@c4-desktop:~$ aplay -l
aplay: device_list:205: no soundcards found...





c4@c4-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
	Subsystem: Gateway 2000 Unknown device 6051
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
	Subsystem: Gateway 2000 Unknown device 6051
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at 30100000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 20e0 [size=8]
	Memory at 20000000 (32-bit, prefetchable) [size=256M]
	Memory at 30180000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Gateway 2000 Unknown device 6051
	Flags: bus master, fast devsel, latency 0, IRQ 9
	Memory at 301c0000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Gateway 2000 Unknown device 6051
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 2080 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Gateway 2000 Unknown device 6051
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 2060 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Gateway 2000 Unknown device 6051
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 2040 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Gateway 2000 Unknown device 6051
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 2020 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: Gateway 2000 Unknown device 6051
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at 301c4000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 30000000-300fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
	Subsystem: Gateway 2000 Unknown device 6051
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: Gateway 2000 Unknown device 6051
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 20b0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Gateway 2000 Unknown device 6051
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at 20c8 [size=8]
	I/O ports at 20ec [size=4]
	I/O ports at 20c0 [size=8]
	I/O ports at 20e8 [size=4]
	I/O ports at 20a0 [size=16]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
	Subsystem: Gateway 2000 Unknown device 6051
	Flags: medium devsel, IRQ 11
	I/O ports at 2000 [size=32]

04:00.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
	Subsystem: Belkin F5D7000 Wireless G Desktop Network Card
	Flags: bus master, slow devsel, latency 32, IRQ 22
	Memory at 30000000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

04:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)
	Subsystem: Gateway 2000 Unknown device 0001
	Flags: bus master, medium devsel, latency 32, IRQ 21
	Memory at 30002000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 1000 [size=64]
	Capabilities: <access denied>

c4@c4-desktop:~$

---

### Post by lyznx on 2008-11-16
It sarted coming out f my speakers again on reboot. Now it is working on my vlc player. but not on the ubuntu main player, whatever its called.
 I guess its a temp patch.

---

### Post by psyke83 on 2008-11-16
You must have screwed something else up on your system.

Why didn't you simply revert the changes you make to the file to see if it helped, rather than reinstalling various packages?

Having said that, the changes to alsa-base would not have affected the loading of your real sound card, so you must have done something else to your system that caused the problem.

---

### Post by erikthedrink on 2009-09-08
I agree something essential may have been removed, yet  you can try this
Go to Applications, then Accessories, then Terminal.  In Terminal, type

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

Then close and re-open your browser (Mozilla Firefox) or restart your system.
:P
Note, if you unplug your desktop speakers, your laptop speakers will take over.  In order to re-establish contact with the desktop speakers, you will need to (plug them back in) restart the system.

---

