---
title: "Problems with ALC272"
date: 2010-12-26
forum: Multimedia Software
---

### Post by d3ngar on 2010-12-26
I have been biting my nails on this problem since more than 8 hours now. I rebuild ALSA twice, got the latest stable version, installed the one from ubuntu-audio-dev, but nothing.

The output from alsa-info.sh can be found here: [http://www.alsa-project.org/db/?f=968f2d4fa4ec74c49dce67747e2f4402acb8c043](http://www.alsa-project.org/db/?f=968f2d4fa4ec74c49dce67747e2f4402acb8c043)

I have this Toshiba and the sound device is just completely messed up and partly depends on if I have headphones plugged into the machine when booting it up: 
Then sometimes everything (Microphone, Headphone, Speakers) works fine. But other times the speakers do not work at all then only the headphones. If I have the headphone not plugged in than in 75% of cases (roughly) the speakers won't go mute when I plug the headphones in.

The microphone(s) is the biggest concern as I need the computer to use Skype. Obviously I would want the jack to work... They sometimes respond when booted, but other times not. They more often work when the microphone jack is plugged in, but fail after a little while, then sometimes they don't work at all.

It frustrating, I have tried various models of the ALC272 driver, but none works for this machine.

Any help with this would be much appreciated...

Chris

---

### Post by d3ngar on 2010-12-29
Just want to bump this thread. I have no idea how to fix it and I can't see any instructions on how to submit issues to ALSA... but I'll check again.

---

### Post by lidex on 2010-12-29
This one can be difficult because both the analog and hdmi use the same module, so i think sometimes they get crossed up and I'm not sure how to load the correct one as default.
You can try reloading alsa when this happens:
```
sudo alsa force-reload
```
You should probably specify a model switch for alsa as well.
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=auto 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by d3ngar on 2010-12-30
Thanks for the info lidex!

Forcing alsa to reload doesn't really do the trick unfortunately, it just keeps the status quo. 

Adding  > options snd-hda-intel model=auto to the alsa-base.conf doesn't solve the problem either. It makes it worse, as alsa seems to restart constantly (I see the speaker going mute and unmute all the time).

What do you mean by '...specify a model switch...'?

I have read in the [ubuntu sound troubleshooting guide]("https://help.ubuntu.com/community/SoundTroubleshooting") that you can stop soundcards from switching. You should see what's available in > /proc/asound/modules and then somehow add them to > /etc/modprobe.d/alsa-base.conf.

Unfortunately the sound cards carry the same name in the modules file... any idea what I could do with that?

Thanks, Chris

---

### Post by lidex on 2010-12-30
Can you post these outputs please:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

I think it would be helpful to install and test a mainline kernel following the directions here:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
The issue may be fixed upstream.

---

### Post by d3ngar on 2011-01-06
Sure will and thanks for your help!

Here is dmidecode -t bios:

> # dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: TOSHIBA
	Version: V1.20
	Release Date: 11/17/2009
	Address: 0xE48D0
	Runtime Size: 112432 bytes
	ROM Size: 1024 kB
	Characteristics:
		PCI is supported
		PNP is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		IEEE 1394 boot is supported
		Smart battery is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
	BIOS Revision: 1.32
	Firmware Revision: 1.32


and here's dmidecode -t baseboard:

> # dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: TOSHIBA
	Product Name: NBWAE
	Version: 1.00
	Serial Number: 0123456789AB

Handle 0x000A, DMI type 10, 6 bytes
On Board Device Information
	Type: Sound
	Status: Disabled
	Description: Realtek HDA-01


Unfortunately the laptop is no longer with me, so I only have access via SSH. Therefore I wouldn't be too keen to play around with the kernel remotely. If something fails I lose access altogether :(...

---

### Post by lidex on 2011-01-07
Three things: bios update, upstream kernel, blacklisting hdmi if you're not using it. The module for that is:
```
snd_hda_codec_hdmi
``` You would just add it to /etc/modprobe.d/blacklist.conf in superuser mode and reboot.

---

### Post by kiai on 2012-07-17
> **lidex said:**
> This one can be difficult because both the analog and hdmi use the same module, so i think sometimes they get crossed up and I'm not sure how to load the correct one as default.
You can try reloading alsa when this happens:
```
sudo alsa force-reload
```You should probably specify a model switch for alsa as well.
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```Insert this line at the bottom:
```
 options snd-hda-intel model=auto 
```Save. Close. Reboot. 

This worked for me. Thank you so much! (Toshiba NB205 with Ubuntu 10.04, RealTek ALC272)  :P

---

### Post by wildmanne39 on 2012-07-19
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

