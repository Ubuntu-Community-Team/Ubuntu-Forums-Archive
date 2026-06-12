---
title: "How do I get surround sound .....nvidia ?"
date: 2014-03-10
forum: Multimedia Software
---

### Post by d.mayfair on 2014-03-10
I am running Xubuntu 13.10 on the following hardware

e-Machines ER1401 mini pc,specs below

[COLOR=#000000]* AMD Athlon™ II Dual Core K325 64 bit[/COLOR]
[COLOR=#000000]* NVIDIA® nForce® 9200 Chipset,[/COLOR]
[COLOR=#000000]* Memory - 2GB DDR3 RAM | 2 x SODIMM slot[/COLOR]
[COLOR=#000000]* Hard Drive - 250GB SATA[/COLOR]
[COLOR=#000000]* Connectivity - hdmi to lcd tv,optical sound output to a/v amplifier

Now although it states nvidia 9200 it is actually 8200 which in theory has 8 channel output.

I can get stereo but not  5.1 which is what I want.

I have installed nvidia driver 319 from the additional drivers list as it is the most recent....there is a newer driver (331) but when I installed it the system hangs.
[/COLOR][COLOR=#000000]I've set the number of channels in pulse to 6 using these commands[/COLOR]

[COLOR=#000000]sudo gedit /etc/pulse/daemon.conf[/COLOR]
[COLOR=#000000]default-sample-channels=6[/COLOR]

[COLOR=#000000]But,I don't get any 5.1 output options in Alsamixer.[/COLOR]

[COLOR=#000000]Help ! [/COLOR]:smile:

[COLOR=#000000]Here's what I get with Alsamixer[/COLOR]

[http://i97.photobucket.com/albums/l2...161519_577.jpg]("http://i97.photobucket.com/albums/l234/stokedaz/IMG_20140310_161519_577.jpg")
[COLOR=#000000]
Cheers



[/COLOR]

---

### Post by d.mayfair on 2014-03-13
I'm convinced the solution is here but I'm too thick to understand :)
[ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html](ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html)

---

### Post by blm-ubunet on 2014-03-14
Your problem is compounded by having one of the first HDMI GPU chipsets (before this was settled/sorted) & by connecting (I assume) the AVR/amp to the TV optical output.

The best arrangement is PC-->amp-->TV but I guess your amp is not HDMI..

If you are very lucky your TV will output AC3 (digital pass thru') but this is if & only if the HDMI input audio is AC3.
It will output 2 ch stereo PCM (as you have now).
It is very unlikely any TV will transcode audio to output over toslink because this has a cost.

The 1st gen HDMI audio codec (as you have) do not support ELD & PD..so you have to manually set/limit the audio capabilities (of the end target device).

I believe the 8200 chipset will output 2 ch stereo/ AC3 & DTS pass thru' & multi-channel PCM.
But your TV will only accept stereo & 448K AC3 & DTS.

Easy to test stereo & multi-channel PCM with "speaker-test" but to test AC3 or DTS you need to use mplayer/vlc etc.
VLC/XBMC/Mythtv can encode to AC3 but you have to point them at the correct output device (iec958).

The later pulse audio is meant to be able to handle AC3/DTS pass thru'.

---

### Post by papibe on 2014-03-14
Hi d.mayfair.

Do you have pulseaudio installed?

Could you post the output of these commands?
```
aplay -l

aplay -L

lspci -nnk | grep -iA2 vga
```
Regards.

---

### Post by d.mayfair on 2014-03-15
> **blm-ubunet said:**
> Your problem is compounded by having one of the first HDMI GPU chipsets (before this was settled/sorted) & by connecting (I assume) the AVR/amp to the TV optical output.

The best arrangement is PC-->amp-->TV but I guess your amp is not HDMI..

If you are very lucky your TV will output AC3 (digital pass thru') but this is if & only if the HDMI input audio is AC3.
It will output 2 ch stereo PCM (as you have now).
It is very unlikely any TV will transcode audio to output over toslink because this has a cost.

The 1st gen HDMI audio codec (as you have) do not support ELD & PD..so you have to manually set/limit the audio capabilities (of the end target device).

I believe the 8200 chipset will output 2 ch stereo/ AC3 & DTS pass thru' & multi-channel PCM.
But your TV will only accept stereo & 448K AC3 & DTS.

Easy to test stereo & multi-channel PCM with "speaker-test" but to test AC3 or DTS you need to use mplayer/vlc etc.
VLC/XBMC/Mythtv can encode to AC3 but you have to point them at the correct output device (iec958).

The later pulse audio is meant to be able to handle AC3/DTS pass thru'.


Thanks for the reply.
My amp does have  hdmi connections but this is what it says in the manual
"in order to receive audio ( including surround sound ) from hdmi sources a co-axial or optical digital audio connection must be made "

As for the tv,it has optical out and hdmi,one of the hdmi's being ARC....i'm not sure how that works to be honest.Here's a link to the tv specs.[http://www.lg.com/uk/tvs/lg-42LA640V](http://www.lg.com/uk/tvs/lg-42LA640V)

---

### Post by d.mayfair on 2014-03-15
> **papibe said:**
> Hi d.mayfair.

Do you have pulseaudio installed?

Could you post the output of these commands?
```
aplay -l

aplay -L

lspci -nnk | grep -iA2 vga
```
Regards.

Here you go

```
daz@daz-ER1401:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
daz@daz-ER1401:~$ aplay -L
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=NVidia
    HDA NVidia, ALC662 rev1 Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
dmix:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Direct sample mixing device
dmix:CARD=NVidia,DEV=1
    HDA NVidia, ALC662 rev1 Digital
    Direct sample mixing device
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=1
    HDA NVidia, ALC662 rev1 Digital
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
hw:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=1
    HDA NVidia, ALC662 rev1 Digital
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=1
    HDA NVidia, ALC662 rev1 Digital
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
daz@daz-ER1401:~$ lspci -nnk l grep -iA2 vga
Usage: lspci [<switches>]


Basic display modes:
-mm		Produce machine-readable output (single -m for an obsolete format)
-t		Show bus tree


Display options:
-v		Be verbose (-vv for very verbose)
-k		Show kernel drivers handling each device
-x		Show hex-dump of the standard part of the config space
-xxx		Show hex-dump of the whole config space (dangerous; root only)
-xxxx		Show hex-dump of the 4096-byte extended config space (root only)
-b		Bus-centric view (addresses and IRQ's as seen by the bus)
-D		Always show domain numbers


Resolving of device ID's to names:
-n		Show numeric ID's
-nn		Show both textual and numeric ID's (names & numbers)
-q		Query the PCI ID database for unknown ID's via DNS
-qq		As above, but re-query locally cached entries
-Q		Query the PCI ID database for all ID's via DNS


Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots
-d [<vendor>]:[<device>]			Show only devices with specified ID's


Other options:
-i <file>	Use specified ID database instead of A2
-p <file>	Look up kernel modules in a given file instead of default modules.pcimap
-M		Enable `bus mapping' mode (dangerous; root only)


PCI access options:
-A <method>	Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>	Set PCI access parameter (see `-O help' for a list)
-G		Enable PCI access debugging
-H <mode>	Use direct hardware access (<mode> = 1 or 2)
-F <file>	Read PCI configuration dump from a given file
daz@daz-ER1401:~$ 
```


Cheers

---

### Post by papibe on 2014-03-15
Thanks.

You didn't say if you have pulseaudio installed. If you have it, you just need to open 'Sound Properties', go to the output tab, and select and 5.1 option in the field 'Mode'.

In case you don't. It's been some time that I play around alsa directly, but I'll try to do my best.

You have 1 physical card and 3 alsa devices. Analog, digital, and HDMI.

In order to use the proper alsa 5.1 output, you need to:
[LIST]
[*]Have an audio source file with multiple channels.
[*]Either select the proper output device on the player itself, or
[*]set it as a default using the alsa conf files.
[/LIST]
[Here]("http://ubuntuforums.org/showthread.php?t=1956187&highlight=nvidia+xbmc")'s is an example of setting default alsa output on XBMC (see post #4)

My guess is that you need to use hw:0,1 (card 0, device 1 which is the digital output).

Hope it helps. Let us know how it goes.
Regards.

---

### Post by d.mayfair on 2014-03-16
I do have pulseaudio but there are no options for 5.1......maybe I have a different version than you because there are no 'sound properties' or 'mode' options either.

In that example you linked to do I copy that code in terminal ?

---

### Post by SeijiSensei on 2014-03-16
I suggest installing **pavucontrol**, the graphical utility for Pulseaudio, from the repositories.  I find that is the simplest solution for managing sound devices, even on the KDE platform I use.

---

### Post by d.mayfair on 2014-03-16
> **SeijiSensei said:**
> I suggest installing **pavucontrol**, the graphical utility for Pulseaudio, from the repositories.  I find that is the simplest solution for managing sound devices, even on the KDE platform I use.


Pavucontrol IS installed.
There are no options there for anything but 2 channels.

---

### Post by SeijiSensei on 2014-03-16
How many different options appear in the Configuration tab?  I admit I don't see 5.1 surround in my list there either, just "Digital Stereo (HDMI Output)," but that may just be because I lack the diligence to pursue it.  I don't use the HDMI audio since it goes directly into my two-channel TV.

---

### Post by d.mayfair on 2014-03-18
> **papibe said:**
> Thanks.

You didn't say if you have pulseaudio installed. If you have it, you just need to open 'Sound Properties', go to the output tab, and select and 5.1 option in the field 'Mode'.

In case you don't. It's been some time that I play around alsa directly, but I'll try to do my best.

You have 1 physical card and 3 alsa devices. Analog, digital, and HDMI.

In order to use the proper alsa 5.1 output, you need to:
[LIST]
[*]Have an audio source file with multiple channels.
[*]Either select the proper output device on the player itself, or
[*]set it as a default using the alsa conf files.
[/LIST]
[Here]("http://ubuntuforums.org/showthread.php?t=1956187&highlight=nvidia+xbmc")'s is an example of setting default alsa output on XBMC (see post #4)

My guess is that you need to use hw:0,1 (card 0, device 1 which is the digital output).

Hope it helps. Let us know how it goes.
Regards.


How/where do I change this setting ?

---

### Post by d.mayfair on 2014-03-19
I have success !!!!!

It was simply a matter of installing a GUI that had the provision for changing settings such as how many channels and which sound device etc.
SMPlayer is the answer.It is highly configurable.

I now have output to all the speakers :)

Now I just have to get my xbmc install to follow suit lol

---

