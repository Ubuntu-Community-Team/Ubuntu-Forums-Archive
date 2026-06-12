---
title: "Sound not working"
date: 2013-02-26
forum: Multimedia Software
---

### Post by Rihoj on 2013-02-26
Hello,

I installed Ubuntu 12.04 LTS on my old toshiba satellite p105-s6084. Well there is no sound when testing, or during start-up. I am not sure what debug information is needed, or where to proceed. I have tried googling, and even tried: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) However I can not get anything to work. . . .I thought, "well lets plug in my headphones maybe my speakers went bad"...  Well I can hear the music extremely faintly, but its there.

Any help??

---

### Post by Yellow Pasque on 2013-02-26
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Rihoj on 2013-02-26
[http://www.alsa-project.org/db/?f=aa42e691d70815f932abadd9bfbe83200493bd3e](http://www.alsa-project.org/db/?f=aa42e691d70815f932abadd9bfbe83200493bd3e)

There is the requested information. Thank you for that first step.

---

### Post by Yellow Pasque on 2013-02-26
I see a few old/expired bug reports for Satellite P105's with that codec. I would first try upgrading the ALSA module to make sure the issue is not already fixed: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

If that does not solve the problem, report it as a bug. Run the info script again and get an updated info link for the bug report.

---

### Post by Rihoj on 2013-03-08
So thank you Temüjin for your help, however the ALSA module did not get it to work. Anyone else having sound troubles, be advised that mine was fixed by updating my bios.

---

### Post by mlichtenstein2 on 2013-03-16
> **Rihoj said:**
> So thank you Temüjin for your help, however the ALSA module did not get it to work. Anyone else having sound troubles, be advised that mine was fixed by updating my bios.

I have the exact problem. How do I update the bios for a Sony Vaio?
After an update to Unbuntu 12.04. With Rhythmbox, I can barely
hear the songs playing with the headphones connected, but nothing with the internal
speakers.

I have a Sony Vaio PCG-7V2l with the following sound card hardware:
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


$ cat /proc/asound/card0/codec* | grep Codec
Codec: SigmaTel STAC9872AK
Codec: Conexant ID 2bfa


The first thing I tried was to run alsamixer and the sound settings for volume control or
mute being set. Everything looks normal and nothing muted. I then updated the sound drivers 
on 03/03/2013 and rebooted:
sudo add-apt-repository ppa:ubuntu-audio-dev
sudo apt-get update
sudo apt-get dist-upgrade

I added 
'options snd-hda-intel index=0 model=vaio"
to the end of /etc/modprobe.d/alsa-base.conf

I also tried adding model=auto and model=generic to alsa-base.conf.

Does anyone have any solutions to this problem?

Thanks,

Mark Lichtenstein
[email]mlichtenstein2@earthlink.net[/email]

---

### Post by mlichtenstein2 on 2013-03-29
Here is some more information about the sound problem with the Sony Vaio
after upgrading with Ubuntu 12.04.

The bottom of the alsa-base.conf file has:

 Prevent abnormal drivers from grabbing index 0
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
# Keep snd-usb-audio from being loaded as first soundcard
options snd-hda-intel model=vaio


But the output from bash "alsa-info.sh --stdout¨ shows both model=auto and model=vaio:
snd-usb-audio: index=-2
snd-hda-intel: model=auto
snd-hda-intel: model=vaio

Where is the model=auto coming from? I found a site that says I need to use
model=vaio

Thanks,

Mark Lichtenstein

---

