---
title: "Audio via Displayport/HDMI with Ubuntu 10.10"
date: 2011-09-06
forum: Multimedia Software
---

### Post by BlackAdderDK on 2011-09-06
Hi

I have an Lenovo TP W520 with Optimus... I have "locked" it to use the Nvidia Quadro 2000M - and everything seems fine - with one exception.. theres no sound with my DisplayPort!

If I boot in Windows, everything works just fine... but in Ubuntu no sound at all

I've tried to follow several post, and I can't get it to work - I'm stuck with the Ubuntu 10.10 as I need iFolder (not working in 11.04)

"aplay -l"
> **** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


"cat /etc/modprobe.d/alsa-base.conf"
> # autoloader aliases
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
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2


In this file several things have been tried according to several post:
> 
# Added by Me part 1
options snd-hda-intel index=0 model=thinkpad
#
# Added by Me part 2
 options snd-hda-intel index=0
#
# Added by Me part 3
 options snd-hda-intel index=auto
#


"lspci -v"
> 01:00.1 Audio device: nVidia Corporation Device 0be9 (rev a1)
    Subsystem: Lenovo Device 21cf
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at d6000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel


"cat /proc/asound/card1/codec#0"
> Codec: Nvidia GPU 11 HDMI/DP
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10de0011
Subsystem Id: 0x10de0101
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="HDMI 0", type="HDMI", device=3
  Converter: stream=6, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04

... and finally I added "ppa:ubuntu-audio-dev/ppa" and updated after this... I even tried to build alsa from source... no succes...

Anyone?

regards

'Adder

---

### Post by BlackAdderDK on 2011-09-06
PS: almost forgot...

"cat /etc/pulse/default.pa"
> #!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore

### Automatically augment property information from .desktop files
### stored in /usr/share/application
load-module module-augment-properties

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack udev support)
load-module module-detect
.endif

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink

### Honour intended role device property
load-module module-intended-roles

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
load-module module-console-kit

### Enable positioned event sounds
load-module module-position-event-sounds

### Cork music streams when a phone stream is active
#load-module module-cork-music-on-phone

# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.

### Load X11 bell module
#load-module module-x11-bell sample=bell-windowing-system

### Register ourselves in the X11 session manager
#load-module module-x11-xsmp

### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif

### Make some devices default
#set-default-sink output
#set-default-source input

Have been editing in "/etc/pulse/default.pa" too:
> 
#Added by Me - part 1
load-module module-alsa-sink device=hw:1,3

#Added by Me - part 2
load-module module-alsa-sink control=PCM

#Changed by Me
from "load-module module-udev-detect" to "load-module module-udev-detect ignore_dB=1"'Adder

---

### Post by BicyclerBoy on 2011-09-06
That audio ppa can be used to update the kernel driver module.
Alsa 1.0.24 user-space seems to be generally recommended.
If you need the 1.0.24 user-space you could try iQuik audio ppa. Possible 10.10 is not supported.
This one has 10.10.
[https://launchpad.net/~ricotz/+archive/unstable?field.series_filter=maverick]("https://launchpad.net/%7Ericotz/+archive/unstable?field.series_filter=maverick")

speaker-test -c 2 -r 48000 -D hw:1,3
speaker-test -c 2 -r 48000 -D hw:1,7
speaker-test -c 2 -r 48000 -D hw:1,8
speaker-test -c 2 -r 48000 -D hw:1,9
if the hw:1,9 works then post
cat /proc/asound/card1/eld#3.0

dmesg | grep HDMI

---

### Post by AbtZ on 2011-09-06
Not sure if it'll help you, but here's what I usually do to enable sound via HDMI:

1. I go to sound preferences (easiest way is to right click the icon in your upper right), and then Hardware tab, and select HDMI as output.

2. I open "alsamixer" in a terminal and, hit F6 to select HDMI sound card and unmute all "S/PDIF" channels.

Always works :)

---

### Post by BlackAdderDK on 2011-09-07
> **BicyclerBoy said:**
> That audio ppa can be used to update the kernel driver module.
Alsa 1.0.24 user-space seems to be generally recommended.
If you need the 1.0.24 user-space you could try iQuik audio ppa. Possible 10.10 is not supported.
This one has 10.10.
[https://launchpad.net/~ricotz/+archive/unstable?field.series_filter=maverick]("https://launchpad.net/%7Ericotz/+archive/unstable?field.series_filter=maverick")

speaker-test -c 2 -r 48000 -D hw:1,3
speaker-test -c 2 -r 48000 -D hw:1,7
speaker-test -c 2 -r 48000 -D hw:1,8
speaker-test -c 2 -r 48000 -D hw:1,9
if the hw:1,9 works then post
cat /proc/asound/card1/eld#3.0

dmesg | grep HDMI


Hi Bicycler

Just tried to add the ppa you suggested... now I can get some white noise out with 1,7... with some "stutter"

"speaker-test -c 2 -r 48000 -D hw:1,7"
> speaker-test 1.0.24.2

Playback device is hw:1,7
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
Write error: -32,Broken pipe
Time per period = 9,948498
 0 - Front Left
Write error: -32,Broken pipe
 1 - Front Right
Write error: -32,Broken pipe
Write error: -32,Broken pipe
Write error: -32,Broken pipe
Write error: -32,Broken pipe
Time per period = 9,360667
 0 - Front Left
 1 - Front Right
Write error: -32,Broken pipe"cat /proc/asound/card1/eld#3.0" (and 0.0 & 2.0)

> monitor_present        0
eld_valid        0"cat /proc/asound/card1/eld#1.0"
> monitor_present        1
eld_valid        1
monitor_name        SAMSUNG
     
connection_type        HDMI
eld_version        [0x2] CEA-861D or below
edid_version        [0x3] CEA-861-B, C or D
manufacture_id        0x2d4c
product_id        0x659
port_id            0x20000
support_hdcp        0
support_ai        0
audio_sync_delay    0
speakers        [0x1] FL/FR
sad_count        1
sad0_coding_type    [0x1] LPCM
sad0_channels        2
sad0_rates        [0xe0] 44100 48000 88200
sad0_bits        [0xe0000] 16 20 24"dmesg | grep HDMI"
> [   15.827501] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
[   16.087122] HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0
[   16.344867] HDMI status: Codec=2 Pin=5 Presence_Detect=0 ELD_Valid=0
[   16.606370] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[   16.726431] input: HDA NVidia HDMI/DP as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input8
[   16.726465] input: HDA NVidia HDMI/DP as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input9
[   16.726494] input: HDA NVidia HDMI/DP as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input10
[   16.726523] input: HDA NVidia HDMI/DP as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[  341.123979] HDMI hot plug event: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=0
[  341.138445] HDMI status: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=0
[  341.204638] HDMI hot plug event: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=1
[  341.218885] HDMI status: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=1
[  343.146446] HDMI: detected monitor SAMSUNG
[  343.146451]       at connection type HDMI
[  343.146457] HDMI: available speakers: FL/FR
[  343.146467] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16 20 24
[  373.188371] HDMI: ASP channel 0 => slot 0
[  373.208368] HDMI: ASP channel 1 => slot 1
[  373.228336] HDMI: ASP channel 15 => slot 2
[  373.248347] HDMI: ASP channel 15 => slot 3
[  373.268298] HDMI: ASP channel 15 => slot 4
[  373.288290] HDMI: ASP channel 15 => slot 5
[  373.308261] HDMI: ASP channel 15 => slot 6
[  373.328238] HDMI: ASP channel 15 => slot 7
[  373.348218] HDMI: ELD buf size is 95
[  373.368204] HDMI: DIP GP[0] buf size is 23
[  373.388180] HDMI: DIP GP[1] buf size is 23
[  373.408166] HDMI: DIP GP[2] buf size is 23
[  373.428147] HDMI: DIP GP[3] buf size is 23
[  373.448123] HDMI: DIP GP[4] buf size is 0
[  373.468107] HDMI: DIP GP[5] buf size is 0
[  373.488086] HDMI: DIP GP[6] buf size is 0
[  373.508056] HDMI: DIP GP[7] buf size is 0regards
'Adder

---

### Post by BlackAdderDK on 2011-09-07
> **AbtZ said:**
> Not sure if it'll help you, but here's what I usually do to enable sound via HDMI:

1. I go to sound preferences (easiest way is to right click the icon in your upper right), and then Hardware tab, and select HDMI as output.

2. I open "alsamixer" in a terminal and, hit F6 to select HDMI sound card and unmute all "S/PDIF" channels.

Always works :)

Thank you, but I all ready tried that :(

regards
'Adder

---

### Post by BicyclerBoy on 2011-09-07
As you have realised..

hw:1,7 & eld#1.0 are inter-connected..

It all looks good except the errors from speaker-test

In /etc/pulse/default.pa change 
#Added by Me - part 1
load-module module-alsa-sink device=**hw:1,3**
to point to **hw:1,7**

& remove everything else you added or changed in this file..
Pulse audio already has a default hw:1,3 sink..

Need to restart the pulse audio server or just logout/in..

---

### Post by BlackAdderDK on 2011-09-08
> **BicyclerBoy said:**
> As you have realised..

hw:1,7 & eld#1.0 are inter-connected..

It all looks good except the errors from speaker-test

In /etc/pulse/default.pa change 
#Added by Me - part 1
load-module module-alsa-sink device=**hw:1,3**
to point to **hw:1,7**

& remove everything else you added or changed in this file..
Pulse audio already has a default hw:1,3 sink..

Need to restart the pulse audio server or just logout/in..

Thanks for all you help - it seems everything is working just great now... Just funny that the native install doesn't include the user-space as it's obviously needed in order to a HDMI/DisplayPort to function

regards
'Adder

---

