---
title: "Sound Card Detection"
date: 2011-05-23
forum: Multimedia Software
---

### Post by thebarisaxkid on 2011-05-23
I have an 82801H HDA Intel card using the snd-hda-intel module. I am on Ubuntu 11.04, installed on a Dell Inspiron 1520. If I play sound, I get an output, however, I am not able to control the volume with the applet on the top panel, or the buttons on that control the volume as well.  I have tried changing the volume in alsamixer, and it does change the volume correctly. If I click Sound preferences or System>Preferences>Sound, a popup says, "Waiting for sound system to respond."

lspci -v
> 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Device 01f1
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


aplay -l
> card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---

### Post by lidex on 2011-05-25
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications-> Accessories-> Terminal"]

---

### Post by thebarisaxkid on 2011-06-25
[http://www.alsa-project.org/db/?f=48838ea212cbd4ecb535a8c0d2afe3fe45d3a0ed](http://www.alsa-project.org/db/?f=48838ea212cbd4ecb535a8c0d2afe3fe45d3a0ed)

*Note* I did this test with Arch Linux because I am testing out different distros.  I am having the same problem with all 64bit OS's.  It should be very similar if not the same. I will also be posting this on the Arch Linux forum, as it would be more relevant there.

---

### Post by lidex on 2011-06-26
Did you try resetting pulse configuration?
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

Your info from above post shows pulse is not running.

---

### Post by thebarisaxkid on 2011-06-30
> **lidex said:**
> Did you try resetting pulse configuration?

Your info from above post shows pulse is not running.

doh!

Yeah, I'm a doofus sometimes. Thanks, solved my problem!

---

