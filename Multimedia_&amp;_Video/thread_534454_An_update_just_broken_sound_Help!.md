---
title: "An update just broken sound? Help!"
date: 2007-08-25
forum: Multimedia &amp; Video
---

### Post by Rob Campbell on 2007-08-25
Hi,

My sound decided to vanish last night from my Thinkpad T40 running Feisty Kubuntu. A large number of KDE updates took place and I wonder if that had anything to do with it. It has always worked in the past.

I've check the volume controls in the mixer and they're all fine. When I try to play music through Amarok it goes through the motions of playing but no sound comes out. I get a bleep when the power cable is unplugged or plugged in. The kcontrol sound test doesn't produce anything but, bizarrely, I can briefly here the test sound if I unplug or re-plug the power connector whilst it's being played. So surely it can 


I have tried:
sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source
sudo apt-get install linux-sound-base alsa-base alsa-utils


And I can report that:
$ uname -r
2.6.20-16-generic

$ cat /proc/asound/modules
 0 snd_intel8x0

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


The end of /etc/modprobe.d/alsa-base contains:

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388



i tried adding: "options snd-intel8x0 index=0" but that didn't help.

Anyone have anything I can try? I've gone through the large audio FAQ I found here and that didn't help.

---

### Post by Rob Campbell on 2007-08-25
Although I had tried re-booting and that didn't help I just cycled the power and that did. Maybe it's just a coincidence but sound now working again. most odd.

---

### Post by jnewm on 2007-09-11
I think the same thing happened on my T40 running regular Ubuntu.  I haven't gotten any sound yet though :(.  By cycling the power, do you mean just holding the power button for ten seconds?  Thanks....

---

### Post by jnewm on 2007-09-11
Excellent!  Recycling the power - unplugging the battery and cable and holding down power for ten seconds - worked for me too!  Weird...  I guess this is a bug, so we should probably report it.  I don't know exactly how, but if I don't hear from Rob (original poster) in a day or so, I'll figure it out.  Thanks again Rob for posting and helping me get my sound back!

---

