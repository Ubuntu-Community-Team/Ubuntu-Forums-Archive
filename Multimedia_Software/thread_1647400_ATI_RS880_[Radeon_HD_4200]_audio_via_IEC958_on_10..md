---
title: "ATI RS880 [Radeon HD 4200] audio via IEC958 on 10.04 LTS"
date: 2010-12-17
forum: Multimedia Software
---

### Post by safarj on 2010-12-17
Hi, this post is for information only. Routing audio via analog output (Internal Audio) works out-of-the-box. To enable IEC958, eg. optical SPDIF output, "Crack of the Day" builds of alsa-driver code found on [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules) has to be installed AND I had to circle multiple times through "Sound preferences" -> Hardware -> choosing "Internal Audio" and click multiple profiles at "Settings for the selected device". The "Digital Stereo (IEC958) Output + Analog Stereo Input" really kicked in only after I chose "Analog Surround .." few times. The HDMI output via RS880 did not work - be it with vanilla 10.04 installation nor after upgrade of alsa-driver as mentioned above. HW list follows:

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci|grep -i audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]

Motherboad is "ASUS M4A88T-V EVO/USB3". Offtopic: USB3 has to be disabled in BIOS in order to make Susped work. There are other ways, but I got no use for USB3 right now.

Keywords for google: S/PDIF, SPDIF

---

### Post by majorw00dy on 2011-02-08
UPDATE:
I was able to get the HDMI port working using the default install of mythbuntu 10.04. First enable IEC958 by going into the mixer (Applications -> Multimedia -> Mixer) change the sound card device to the HDMI version. Click and enable IEC958. Then create /etc/asound.conf and add the following lines;

> 

pcm.!default {
	type hw
	card 1
	device 3
}


OR

> 

pcm.!default {
	type plug slave.pcm {
		type hw card 1 device 3
	}
}




The card number and device number were taken from 'aplay -l'

> 
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card [COLOR="Navy"]1[/COLOR]: HDMI [HDA ATI HDMI], device [COLOR="Navy"]3[/COLOR]: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0




For more alsa information visit: [http://alsa.opensrc.org/FAQ026](http://alsa.opensrc.org/FAQ026)

---

### Post by safarj on 2011-02-08
Cool! Thank you for :)

---

