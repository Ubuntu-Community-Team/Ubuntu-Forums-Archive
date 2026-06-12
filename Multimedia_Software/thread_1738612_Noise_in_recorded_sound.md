---
title: "Noise in recorded sound"
date: 2011-04-25
forum: Multimedia Software
---

### Post by eyden on 2011-04-25
Hello everyone,

I'm running Ubuntu 10.10 in a Samsung R510. I've tried to record sound with an external microphone and there have always been a permanent noise accompanying it.
I thought it could be the internal microphone, that's causing the noise, but even when I disabled it the noise remains. Or maybe I didn't disable it the right way !


Any help would be appreciated.

Many thanks

---

### Post by lidex on 2011-04-28
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by eyden on 2011-04-28
Thanks.
Output as attachement

---

### Post by lidex on 2011-04-28
Some motherboard info please:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by eyden on 2011-04-28
sudo dmidecode -t bios

```

# dmidecode 2.9
SMBIOS 2.5 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Phoenix Technologies Ltd.
	Version: 10LI.M008.20100401.KSJ
	Release Date: 04/01/2010
	Address: 0xE4CD0
	Runtime Size: 111408 bytes
	ROM Size: 2048 kB
	Characteristics:
		ISA is supported

		PCI is supported


		PC Card (PCMCIA) is supported
		PNP is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		ACPI is supported
		USB legacy is supported
		AGP is supported
		Smart battery is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
	BIOS Revision: 0.
```


sudo dmidecode -t baseboard

```
# dmidecode 2.9
SMBIOS 2.5 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: SAMSUNG ELECTRONICS CO., LTD.
	Product Name: R510/P510                  
	Version: Not Applicable
	Serial Number: 123490EN400015

Handle 0x000B, DMI type 10, 6 bytes
On Board Device Information
	Type: Sound
	Status: Disabled
	Description: HD-Audio



```

---

### Post by lidex on 2011-04-28
Try gnome-alsamixer.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Here are your controls:
```
Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xf6200000 irq 46'
  Mixer name	: 'Nvidia MCP77/78 HDMI'
  Components	: 'HDA:10ec0262,144dc042,00100202 HDA:10de0003,10de0101,00100000'
  Controls      : 23
  Simple ctrls  : 13
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 16 [52%] [-22.50dB] [on]
  Front Right: Playback 16 [52%] [-22.50dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'Speaker',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 250 [98%] [-1.00dB]
  Front Right: Playback 250 [98%] [-1.00dB]
[COLOR="Red"]Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off][/COLOR]
[COLOR="Red"]Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%] [30.00dB]
  Front Right: 3 [100%] [30.00dB][/COLOR]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
[COLOR="Red"]Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 11 [35%] [4.50dB] [off]
  Front Right: Capture 11 [35%] [4.50dB] [off][/COLOR]
[COLOR="Red"]Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [34.50dB] [off]
  Front Right: Capture 29 [94%] [31.50dB] [off][/COLOR]
[COLOR="Red"]Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-12.00dB] [off]
  Front Right: Capture 0 [0%] [-12.00dB] [off][/COLOR]
[COLOR="Red"]Simple mixer control 'Internal Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off][/COLOR]
[COLOR="Red"]Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%] [30.00dB]
  Front Right: 3 [100%] [30.00dB][/COLOR]
```
Basically you want the channel, capture and boost for the mic input enabled and properly adjusted, while disabling the others.

---

### Post by eyden on 2011-04-29
Thank you so much for your help. Unfortunately using gnome-alsamixer to adjust controls didn't help. I even replaced Pulsaudio with Alsa and it didn't help.
How could I disable the internal microphone ? I think it's causing the noise

---

### Post by lidex on 2011-04-29
Try setting your Internal Mic Boost to zero.

---

### Post by eyden on 2011-05-01
setting the mic boost to zero didn't help.
Here are my controls settings. Is there a difference between Capture and digitale ? By recording from sound recorder it doesn't make a big difference choosing the one or the other as input source.

BTW I'm running Mint 10.10 now and getting the same issue.

---

### Post by lidex on 2011-05-01
Digital would probably be internal.
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=ultra" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by eyden on 2011-05-01
I've got new controls and input sources ( Microphone ). Recording using microphone as input source is even worse, I just can hear the noise but no voice.

 In gnome-alsamixer it is possible to adjust the microphone.Otherwise, launching  "alsamixer" from terminal shows, that the microphone is not enabled and I have no option to enable it.

PLease see attachement.

---

