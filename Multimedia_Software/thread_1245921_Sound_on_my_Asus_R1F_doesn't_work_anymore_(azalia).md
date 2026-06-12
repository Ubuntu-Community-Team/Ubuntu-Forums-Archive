---
title: "Sound on my Asus R1F doesn't work anymore (azalia)"
date: 2009-08-21
forum: Multimedia Software
---

### Post by samathyr on 2009-08-21
Hi!

I am having a problem with my soundcard... I have been checking the forum but I haven't seen anything similar.

I got an Asus R1F - tablet PC, which I think is one of the best tablets in the market. I am using **Intrepid Ibex (8.10)** and I managed to configure the touchscreen.
[IMG]http://www.asus.com/websites/global/products/ybwWQBLekJkbQGnB/P_100.jpg[/IMG]

**The sound card was detected and working without problems since the first boot. **

However, when I was about to finish all the customization work and to backup everything in an external hard disk... I discovered that the sound was not working anymore.

Whenever I listened to any sound, for instance a youtube video or a song with VLC, I** heard a sound which is like something sparkling**, it ends when I close the program playing the sound. 

The last thing I did when I spot this problem was to delete the AMAROK, install a .deb with libxine1-ffmpeg because I was not able to install it from synaptic (it doesn't work properly, sometimes it frezees) and then updating it and installing Amarok alltogether.

According to Asus website, the audio is:
Built-in Azalia compliant audio chip, with 3D effect & full duplex
Built-in speaker and microphone
ADSP

And I think it uses a Realtek chipset (as I have seen in other posts).

Could you help me with this problem? 
I could start from scratch... but I have done it twice already (Windows Vista deleted my ext3 partition last Wednesday...), but let's see if I can make it this time :D
Thanks

---

### Post by Favux on 2009-08-21
Hi samathyr,

Are you sure about the sound card?  Check by entering in a terminal:
```
aplay -l
```
I think it is an Intel sound chip

The one line I've seen is:
```
options snd-hda-intel model=asus
```
Which you add to the end of alsa-base.
```
gksudo gedit /etc/modprobe.d/alsa-base
```
You could look into it anyway.

---

### Post by samathyr on 2009-08-21
This is all the information I can get by now :-(

```
luis@luis-tablet:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC660-VD Analog [ALC660-VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


from lspci -v
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)                                                        
        Subsystem: ASUSTeK Computer Inc. Device 1339                           
        Flags: bus master, fast devsel, latency 0, IRQ 16                      
        Memory at fe138000 (64-bit, non-prefetchable) [size=16K]               
        Capabilities: <access denied>                                          
        Kernel driver in use: HDA Intel                                        
        Kernel modules: snd-hda-intel     
```

```
speaker-test 1.0.17

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 2048 to 8192
Period size range from 1024 to 1024
Using max buffer size 8192
Periods = 4
was set period_size = 1024
was set buffer_size = 8192
 0 - Front Left
Time per period = 2.835858
 0 - Front Left
Time per period = 2.986596
 0 - Front Left
Time per period = 2.986607
 0 - Front Left
Time per period = 2.986631
 0 - Front Left
...

```

and a neverending list. it never stops testing.

I've tried the 2 phones outputs and the laptop speakers. Neither works... :S

In System > Preferences > Sound I've just have tried to check all of the possible setting and nothing!

:-(

I add that line to gksudo gedit /etc/modprobe.d/alsa-base, and nothing... I am trying to come back to copy and paste that file in here, but it frezees :-( I am getting really pissed (do you really want to look at it?) I am thinking about flashing BIOS, formatting everything and start from scratch for the 3r time (5th in total)... the Vista thing as enraged me in such a way that now I really hate Microsoft viscerally... it is very frustrating.

**pd: Another fact about this thing is that the OSD display of the FN keys when I decrease or increase the volume appears with an icon which is not a little bit bigger than before, and a little pixelated **
Like this
[IMG]http://img44.imageshack.us/img44/4708/63984380.png[/IMG][IMG]http://img44.imageshack.us/img44/4827/96678027.png[/IMG]

EDIT!


Here you can see my etc/modprobe.d/alsa-base (the last line is added since the last post)
```
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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
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
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel model=asus
```

---

### Post by Favux on 2009-08-21
Hi samathyr,

Well it's definitely Intel from aplay and lspci.  It looks like you edited alsa-base correctly.  You tried the line and rebooted?

Unfortunately I'm not a sound guru.  I already looked at the snd-hda-intel thread and they don't have a line for the R1F.  A bunch of other ASUS yes, but not the R1F.

---

### Post by samathyr on 2009-08-23
any ideas ? 

I am not able to fix it ..........

I think I think I will start from scratch tomorrow

---

### Post by Favux on 2009-08-23
Hi samathyr,

Well looking in ALSA-Configuration.txt (which should be somewhere on your system in compressed form called ALSA-Configuration.txt.gz) the beginning Intel section says:
```
Module snd-hda-intel
  --------------------

    Module for Intel HD Audio (ICH6, ICH6M, ESB2, ICH7, ICH8),
		ATI SB450, SB600, RS600,
		VIA VT8251/VT8237A,
		SIS966, ULI M5461

    [Multiple options for each card instance]
    model	- force the model name
    position_fix - Fix DMA pointer (0 = auto, 1 = use LPIB, 2 = POSBUF)
    probe_mask  - Bitmask to probe codecs (default = -1, meaning all slots)
    bdl_pos_adj	- Specifies the DMA IRQ timing delay in samples.
		Passing -1 will make the driver to choose the appropriate
		value based on the controller chip.
    
    [Single (global) options]
    single_cmd  - Use single immediate commands to communicate with
		codecs (for debugging only)
    enable_msi	- Enable Message Signaled Interrupt (MSI) (default = off)
    power_save	- Automatic power-saving timtout (in second, 0 =
		disable)
    power_save_controller - Reset HD-audio controller in power-saving mode
		(default = on)

    This module supports multiple cards and autoprobe.
    
    Each codec may have a model table for different configurations.
    If your machine isn't listed there, the default (usually minimal)
    configuration is set up.  You can pass "model=<name>" option to
    specify a certain model in such a case.  There are different
    models depending on the codec chip.
```
And then going down to what I think is your chip set section:
```
	ALC861/660
	  3stack	3-jack
	  3stack-dig	3-jack with SPDIF I/O
	  6stack-dig	6-jack with SPDIF I/O
	  3stack-660	3-jack (for ALC660)
	  uniwill-m31	Uniwill M31 laptop
	  toshiba	Toshiba laptop support
	  asus		Asus laptop support
	  asus-laptop	ASUS F2/F3 laptops
	  auto		auto-config reading BIOS (default)
```
So you could try some of the other options and see if they work.

Some other links R1F links:
[http://ubuntuforums.org/showthread.php?t=918886](http://ubuntuforums.org/showthread.php?t=918886)

[http://forum.tabletpcreview.com/showthread.php?p=160334](http://forum.tabletpcreview.com/showthread.php?p=160334)

and a R1E
[https://help.ubuntu.com/community/AsusR1E](https://help.ubuntu.com/community/AsusR1E)

---

