---
title: "Internal microphone not working for HDA Intel ALC269"
date: 2011-04-02
forum: Multimedia Software
---

### Post by ferrouille on 2011-04-02
Hi all,
I just installed ubuntu 10.10 about 10 days ago, an experience that has been both amazing because its really hard for me to go back to windows already, and frustrating because I'm having a little issue: my internal microphone is not working.

here is some relevant info:
I had alsa 1.0.23 and decided to upgrade thinking it would solve my problems so I ran the script to install 1.0.24, and for a day or two I lost my sound, without getting back my mic, and just like that the sound came back.

I read a lot of posts out there, and ,ade sure I unmuted my mic in alsa soundmixer and pulseaudio.

here is some additional info:
[http://www.alsa-project.org/db/?f=de887e8cfc4659e3320ed51f30db476094f89e0e](http://www.alsa-project.org/db/?f=de887e8cfc4659e3320ed51f30db476094f89e0e)

I ran this:
sudo aplay -l
result:
card 0: Intel [HDA Intel], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

that is kind of weird because I'm positive that this command would return ALC259 under alsa 1.0.23... 

also I ran: ls /etc/modprobe.d
and the result is:
alsa-base.conf           blacklist-framebuffer.conf
alsa-base.save           blacklist-modem.conf
alsa-base.save.1         blacklist-oss.conf
blacklist-ath_pci.conf   blacklist-watchdog.conf
blacklist.conf           intel-5300-iwlagn-disable11n.conf
blacklist-firewire.conf

finally here is the alsa-base.conf content:
# autoloader aliases
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
# Specify soundcard
options snd-hda-intel model=laptop-amic position_fix=0

your experienced thoughts are much appreciated

---

### Post by lidex on 2011-04-02
I want you to edit alsa-base.conf to **remove** this line:
```
options snd-hda-intel model=laptop-amic position_fix=0
```
To open:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Save it then delete these items:
```
sudo rm -r alsa-base.save alsa-base.save.1
```
Now reboot.

With aplay sudo is not needed and best run without it.

---

### Post by ferrouille on 2011-04-03
thanks lidex - I did all the above without seeing any success.
in fact I am now without sound or microphone. 

any thoughts as to what are my other options?

---

### Post by lidex on 2011-04-03
Rerun the info script please.
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by ferrouille on 2011-04-03
here it is:
[http://www.alsa-project.org/db/?f=e8bb59272ba6e014eeba1b61c9389d3e16b718e3](http://www.alsa-project.org/db/?f=e8bb59272ba6e014eeba1b61c9389d3e16b718e3)

---

### Post by lidex on 2011-04-03
Play around with these models in alsa-base.conf, one at a time please:
```
auto
lifebook
basic		
quanta	
eeepc-p703	
eeepc-p901	
fujitsu	
```
In this format:
```
options snd-hda-intel model=
```
Reload alsa after each change is saved:
```
sudo alsa force-reload
```

---

### Post by ferrouille on 2011-04-05
Lidex,
the first attempt with AUTO as the model was the good one - thanks so much for the help!!!
party time on my ubuntu now :):popcorn:
t

---

### Post by lidex on 2011-04-05
You're welcome!

---

