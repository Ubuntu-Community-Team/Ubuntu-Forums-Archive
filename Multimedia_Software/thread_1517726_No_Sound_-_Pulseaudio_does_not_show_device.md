---
title: "No Sound - Pulseaudio does not show device"
date: 2010-06-25
forum: Multimedia Software
---

### Post by reef2dive on 2010-06-25
I have a Toshiba U500 where the sound has been lost since the upgrade to Ubuntu 10.04 - Lucid Lynx.

The sound works when using aplay. The sound device is not listed in pulseaudio. See attached image.
I have been through the following setup "HOWTO: PulseAudio Fixes & System-Wide Equalizer Support" [http://ubuntuforums.org/showthread.php?t=789578&referrerid=80902](http://ubuntuforums.org/showthread.php?t=789578&referrerid=80902).

When I do
```
test@ubuntu-lucid:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
Home directory /home/test not ours.
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC269 Digital [ALC269 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
I get all the devices. To me this means that the device is recognized. 

And using the command
```
test@ubuntu-lucid:~$ aplay -Dplughw:0,0 -fcd Downloads/assume.wav 
Warning: format is changed to U8
Playing WAVE 'Downloads/assume.wav' : Unsigned 8 bit, Rate 11025 Hz, Mono
```
plays nicely. :p

Other print-outs are:

```
dpkg -l | grep "alsa"
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-oss                              1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA
ii  libsox-fmt-alsa                       14.3.0-1.1build1                                SoX alsa format I/O library
```

For the below command, only the sound related are shown
```
sudo lspci -v 
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff41
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fddf8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

08:00.1 Audio device: ATI Technologies Inc RV710/730
	Subsystem: Toshiba America Info Systems Device ff40
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at febec000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [100] Vendor Specific Information <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```


```
test@ubuntu-lucid:~$ fgrep -ie 'audio' /etc/group
audio:x:29:pulse

```

On another laptop with a similar problem
```
sudo alsa force-reload
```
used to force the devices to show up and in this case it does not work.

Any tips? Is it an issue with pulseaudio or with ALSA?

---

### Post by lidex on 2010-06-25
Have you tried this:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**

Check the permissions on your user folder also.

---

### Post by reef2dive on 2010-06-26
Thank you 

The use of these commands are in "HOWTO: PulseAudio Fixes & System-Wide Equalizer Support". So it had been done once
```
rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
In this case the .pulse directory existed and deleted. The other dir or file did not exist.

No result on this one.

I think I need to force pulseaudio to recognize all the devices.

Regarding the permission, I do not understand what is expected, as this is something I have not changed.
```
drwxr-xr-x 72 test test  4096 2010-06-26 07:22 test
```

---

### Post by reef2dive on 2010-07-31
When using the live Ubuntu 9.10, the sound works fine. All devices are recognized.
I have been checking all files related to the sound setup and they look the same. The only difference is that the start of pulseaudio is difference in 10.04 is the start-up.

When comparing the pulseaudio setup using [pacmd - Reconfigure a PulseAudio sound server during runtime
]
```
pacmd
```
For 10.04, the result is
```
>>> list-cards
1 card(s) available.
    index: 0
	name: <alsa_card.pci-0000_08_00.1>
	driver: <module-alsa-card.c>
	owner module: 4
	properties:
		alsa.card = "1"
		alsa.card_name = "HDA ATI HDMI"
		alsa.long_card_name = "HDA ATI HDMI at 0xfebec000 irq 17"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:08:00.1"
		sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:08:00.1/sound/card1
"
		device.bus = "pci"
		device.vendor.id = "1002"
		device.vendor.name = "ATI Technologies Inc"
		device.product.id = "aa38"
		device.product.name = "RV710/730"
		device.string = "1"
		device.description = "RV710/730"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	profiles:
		output:hdmi-stereo: Digital Stereo (HDMI) Output (priority 5400)
		off: Off (priority 0)
	active profile: <output:hdmi-stereo>
	sinks:
		alsa_output.pci-0000_08_00.1.hdmi-stereo/#0: RV710/730 Digital Stereo (HDMI)

	sources:
		alsa_output.pci-0000_08_00.1.hdmi-stereo.monitor/#0: Monitor of RV710/730 Digital Stereo (HDMI)

```
while the same command in 9.10 live version gives
```

>>> list-cards
2 card(s) available.
    index: 0
	name: <alsa_card.pci-0000_08_00.1>
	driver: <module-alsa-card.c>
	owner module: 4
	properties:
		alsa.card = "1"
		alsa.card_name = "HDA ATI HDMI"
		alsa.long_card_name = "HDA ATI HDMI at 0xfebec000 irq 17"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:08:00.1"
		sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:08:00.1/sound/card1"
		device.bus = "pci"
		device.vendor.id = "1002"
		device.vendor.name = "ATI Technologies Inc"
		device.product.id = "aa38"
		device.product.name = "R700 Audio Device [Radeon HD 4000 Series]"
		device.string = "1"
		device.description = "R700 Audio Device [Radeon HD 4000 Series]"

		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	profiles:
		output:hdmi-stereo: Digital Stereo (HDMI) Output (priority 5400)
		off: Off (priority 0)
	active profile: <output:hdmi-stereo>
	sinks:
		alsa_output.pci-0000_08_00.1.hdmi-stereo/#0: R700 Audio Device [Radeon HD 4000 Series] Digital Stereo (HDMI)
	sources:
		alsa_output.pci-0000_08_00.1.hdmi-stereo.monitor/#0: Monitor of R700 Audio Device [Radeon HD 4000 Series] Digital Stereo (HDMI)
    index: 1
	name: <alsa_card.pci-0000_00_1b.0>
	driver: <module-alsa-card.c>
	owner module: 5
	properties:
		alsa.card = "0"
		alsa.card_name = "HDA Intel"
		alsa.long_card_name = "HDA Intel at 0xfddf8000 irq 22"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1b.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.id = "293e"
		device.product.name = "82801I (ICH9 Family) HD Audio Controller"
		device.form_factor = "internal"
		device.string = "0"
		device.description = "Internal Audio"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	profiles:
		output:analog-stereo: Analog Stereo Output (priority 6000)
		output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (priority 6060)
		output:iec958-stereo: Digital Stereo Duplex (IEC958) (priority 5500)
		output:iec958-stereo+input:analog-stereo: Digital Stereo (IEC958) Output + Analog Stereo Input (priority 5560)
		input:analog-stereo: Analog Stereo Input (priority 60)
		off: Off (priority 0)
	active profile: <output:analog-stereo+input:analog-stereo>
	sinks:
		alsa_output.pci-0000_00_1b.0.analog-stereo/#1: Internal Audio Analog Stereo
	sources:
		alsa_output.pci-0000_00_1b.0.analog-stereo.monitor/#1: Monitor of Internal Audio Analog Stereo
		alsa_input.pci-0000_00_1b.0.analog-stereo/#2: Internal Audio Analog Stereo

```
There is a difference in the start-up of pulseaudio in 10.04 vs. 9.10. There is a start-up file in
```

/etc/xdg

```
in 10.04.
Is there any information how the start-up of pulseaudio actually works in Ubuntu?
Is there any command where I can force the card to be loaded in pulseaudio?

---

### Post by reef2dive on 2010-08-06
Found the issue with great support.
```
echo autospawn = no >> ~/.pulse/client.conf
killall pulseaudio
LANG=C pulseaudio -vvvv > ~/pulseverbose.log 2>&1
```
and
```
sudo fuser -v /dev/snd/*
```
made me found conflicting applications at boot

---

### Post by lidex on 2010-08-06
If you don't mind telling us what the conflict was and how you resolved it?

---

### Post by reef2dive on 2010-08-08
The application that interfered with pulseaudio, was randomsound through arecord. Apparently in the bootup randomsound locks the device prior to pulseaudio.
Randomsound was removed through apt, and it fixed the problem.

Maybe it is possible to change the order at boot.
(Randomsound makes a big difference in the entropy-pool on this machine)

---

### Post by a-user on 2010-09-08
i have nearly the same issue but in my case i did not have randomsound installed.

i have recently updated maverick beta. the first days after beta install my onboard soundcard and my hdmi device of my gt220 where found by pulse. after some updates suddendly i observed no sound. in the list of found device only my onboard sound was found (and my dvb-s card).

aply -l showed all cards, so did aslamixer.

i found out that there are 2 ways to get sound back:
1. log out, log in as a different user (must be a different one!), log out again and login to the first one. (it does not matter if you do the same with both users switched. it must be a user change)

2. killall pulsaudio being logged in and restart it.

i tried as it has been suggested here to find conflicting programms but there is nothing to be found.

any idea?

EDIT: i thought about what i had different to my previous ubuntu 9.10 setup. i have a java app starting automatically uppon login. this time im using openjava where i previously used sun. i removed the autostart of the java programm and ... tada... hdmi device found.

is there anyway to control te order of startupprogramms duing login? or any other idea how tto prevent such problems?

ED: well i tried using sun-java (had to add lucid partner repo -.-) but same happens. so it does not matter what java engine is used. but starting it during login automatically provokes the issue.

---

