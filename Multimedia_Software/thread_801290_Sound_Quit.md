---
title: "Sound Quit"
date: 2008-05-20
forum: Multimedia Software
---

### Post by Velcro39 on 2008-05-20
I went through the Comprehensive Sound Problems Solution Guide and was unable to get my sound to work again. My sound was working fine until I uninstalled all ndiswrapper packages trying to fix a wifi card issue.

It is a Dell Inspiron 8200 with the following sound card according to lspci:

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
	Subsystem: Cirrus Logic Crystal WMD Audio Codec
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at d800 [size=256]
	I/O ports at dc80 [size=64]

I have tried both fixes in the Guide mentioned above. I am very new to Linux and even newer to Ubuntu (Hardy). I wasn't quite sure which driver to install using the alsa-source method so I tried installing the only two Intel drivers listed. Maybe the wrong driver?

I don't know. Please help. Thanks a bunch.

---

### Post by xc3RnbFO8P on 2008-05-20
I would make a fresh install of Hardy Heron.

---

### Post by Velcro39 on 2008-05-20
A second restart to backup my data to do just that and suddenly the sound works. Why it took a second restart I do not know. And I got my wifi to work too.

---

