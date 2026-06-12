---
title: "Gasp! Another person with a sound issue (intel8x0)"
date: 2007-08-08
forum: Multimedia &amp; Video
---

### Post by aliencam on 2007-08-08
**The Issue: **
[INDENT]I cannot get any sound, I have tried just about every community database help related to sound issues, and have looked through the forums extensively. [/INDENT]

**System Specs**
Gigabyte K8NSNXP (my box says K8N-Pro ;not listed on their site, k8nsnxp is same)
nForce 3 Chipset
AWARD Bios
AMD 64 3200+
ATI Radeon 9800 Pro (AGP)
2GB DDR (2DIMMs) 
Creative Sound Blaster Audigy X-Fi (no drivers, i'm not even trying to get that to work, its just there)
I am using Feisty Fawn Ubuntu

My motherboard's audio is AC97, or Realtek ALC850. the driver should be snd-intel8x0
[B]
What I've Tried So Far[/B]
#[URL="https://help.ubuntu.com/community/DebuggingSoundProblems?highlight=%28sound%29"]DebuggingSoundProblems
[/URL]
#[URL="https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28sound%29"]HdaIntelSoundHowTo
[/URL]
#[SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28sound%29")



[B]
output of "aplay -l"[/B] 
```
cameron@cameron-desktop:~$ aplay -l


********************   WARNING   *******************************
Warning! aplay uses ALSA emulation instead of the native OSS API
****************************************************************

**** List of PLAYBACK Hardware Devices ****
card 1: snd_ctl_card_info_get_id [Nvidia nForce3], device 0: OSS ID [Nvidia nForce3]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [Nvidia nForce3], device 1: OSS ID [Nvidia nForce3 S/PDIF out]
  Subdevices: 1/1
  Subdevice #0: OSS subname

```





[B]
output of alsamixer[/B][COLOR="Red"] (i think this has something to do with the problem but i have tried reinstalling and it doesn't fix it)[/COLOR]
```
alsamixer: relocation error: alsamixer: symbol snd_mixer_selem_get_playback_dB, version ALSA_0.9 not defined in file libasound.so.2 with link time reference
                                                                            cameron@cameron-desktop:~$ 


```
once the above happens, my name is wrapped in the terminal, it starts on the right side and wraps around to a new line, i cannot type anything else in, everything above that command is gone, i have to close the terminal and try again. 


**output of lspci -v **
```
cameron@cameron-desktop:~$ lspci -v
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at <ignored> (32-bit, prefetchable)
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
        Subsystem: Giga-byte Technology Unknown device 0c11
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
        Subsystem: Giga-byte Technology Unknown device 0c11
        Flags: 66MHz, fast devsel, IRQ 9
        I/O ports at 1c00 [size=64]
        I/O ports at 2000 [size=64]
        Capabilities: <access denied>

00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
        Subsystem: Giga-byte Technology Unknown device a002
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        I/O ports at b400 [size=256]
        I/O ports at b800 [size=128]
        Memory at fa001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

01:07.0 Multimedia video controller: NEC Corporation Dual Tuner/MPEG Encoder (rev 0c)
        Subsystem: Lumanate, Inc. Unknown device 001b
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at f5204000 (32-bit, non-prefetchable) [size=8K]
        Memory at f5208000 (32-bit, non-prefetchable) [size=512]
        Capabilities: <access denied>

01:08.0 Multimedia audio controller: Creative Labs SB X-Fi
        Subsystem: Creative Labs X-Fi XtremeMusic
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at 9000 [size=32]
        Memory at f5000000 (64-bit, non-prefetchable) [size=2M]
        Memory at f0000000 (64-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>

```
I just deleted everything from lspci -v that had nothing to do with this, otherwise the post would be insanely long(er than it already will be) and i couldn't find a collapse tag for these forums (is there one installed here?)



**output of sudo modprobe**

```
cameron@cameron-desktop:~$ sudo modprobe snd-intel8x0
FATAL: Module snd_intel8x0 not found.
cameron@cameron-desktop:~$ sudo modprobe snd-intel8x0m
FATAL: Module snd_intel8x0m not found.

```


now, because it says that module (snd-intel8x0) could not be found, and that is the driver listed on the alsa website for nForce chipsets i would try to reinstall from a "fresh" kernel as instructed to by [SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28sound%29")
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```

```
sudo apt-get install linux-sound-base alsa-base alsa-utils 
sudo apt-get install gdm ubuntu-desktop
```

reboot, and try aplay -l again. .. and i get the same output as the first time. 
```
cameron@cameron-desktop:~$ aplay -l


********************   WARNING   *******************************
Warning! aplay uses ALSA emulation instead of the native OSS API
****************************************************************

**** List of PLAYBACK Hardware Devices ****
card 1: snd_ctl_card_info_get_id [Nvidia nForce3], device 0: OSS ID [Nvidia nForce3]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [Nvidia nForce3], device 1: OSS ID [Nvidia nForce3 S/PDIF out]
  Subdevices: 1/1
  Subdevice #0: OSS subname

```


sound still does not work, alsamixer still does not work, sudo modprobe snd-intel8x0 still does not work,  and i get the same thing when i download and install the drivers new and i still get the same issues...  at this point the community doccumentation wiki article "SoundTroubleshooting" instructs me to create a new thread that is what this is)   so yeah... any more suggestions???


EDIT ADD: 
I just removed the sound blaster audigy card from my computer, and double-checked the BIOS Settings, AC97 Audio Controller is on "Auto", the options are "Auto" or "Off", so I re-selected Auto. I then compiled new ALSA Drivers using these commands: 

```
sudo mkdir /usr/src/alsa
cd /usr/src/alsa
sudo apt-get install build-essential linux-headers-$(uname -r)
sudo wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc4.tar.bz2
sudo tar -xvjf alsa-driver-1.0.14rc4.tar.bz2
cd alsa-driver-1.0.14rc4
sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=intel8x0 --with-oss=yes
sudo make
sudo make install
```

This went through with no errors, but still no sound.  and still when i run sudo modprobe snd-intel8x0 i get module not found, and that alsamixer error... how is this possible after rebuilding the drivers from source!??!

The attached image pretty much summarizes all of my problems (or what i think my problems are... for all i know its something completely different screwing me up.)

---

### Post by th0r0n on 2007-09-10
BUMP

I am having the EXACT same problem.

T

---

