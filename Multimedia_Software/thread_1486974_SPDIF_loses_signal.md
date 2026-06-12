---
title: "SPDIF loses signal"
date: 2010-05-18
forum: Multimedia Software
---

### Post by Murderlove on 2010-05-18
Dear readers,

I have been using Linux on and off. I have just installed Ubuntu 10.04  via the Wubi installer. I have come across a problem which I can not  solve on my own. I therefor need your kind help.

This is my setup:
Asus Xonar Essence STX soundcard --> optical/SPDIF connection-->  DAC--> RCA-connection--> Amplifier--> RCA connection--> 2  speakers and a subwoofer.

 I have installed the latest ALSA drivers via this method:
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)
and selected the STX as my  default soundcard. I have disabled the onboard sound via the BIOS.

Here is my problem:
I have been able to get sound, both analog as well as digital. However my  DAC displays that I do not have a signal until I play a soundfile. The  moment I play a soundfile, the DAC displays 44.1KHz, then I hear a  crackling/thunder sound for just a few seconds and then the soundfile  plays. The crackling/thunder sound is there for only a few seconds, but  it is really annoying. 

What worries me is that my DAC displays that I do not have a signal  unless I play a soundfile. It is as if the SPDIF/optical output is put  into hibernation untill a sound is being played. Because of a certain  cable I use I can see when the SPDIF/optical output is on, or off. A  light will go on when the output is on. When I am not playing a  soundfile the DAC somehow loses connection and restarts when a sound is  being played.

I have tested this with oboard sound as well and I have the exact same  problem.

My question to you is: what do I need to do so that the SPDIF/optical  output won't loose signal but remains on all the time? That crackling  sound is really annoying.

I look forward hearing from you.

PS: the above described problem is not there in windows.

---

### Post by Murderlove on 2010-05-19
Bump

---

### Post by lidex on 2010-05-20
Can you post output from this command:
```
cat /etc/modprobe.d/alsa-base.conf
```

---

### Post by Murderlove on 2010-05-20
Thank you for your reply. This is what it shows:
murderlove@ubuntu:~$ cat /etc/modprobe.d/alsa-base.conf
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
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
murderlove@ubuntu:~$ 

A picture of what I am seeing in alsamixer:
[[url=http://www.plaatjesupload.nl/bekijken/2661721.html][img]http://www.plaatjesupload.nl/bekijk/2010/05/20/1274353002-50.png[/img]]("http://www.plaatjesupload.nl/bekijken/2661718.html")
[/URL]

---

### Post by Murderlove on 2010-05-24
Bump.

---

### Post by lidex on 2010-05-25
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by Murderlove on 2010-05-29
Thank you for your reply. I am currently rearranging my sound setup. I may remove the amplifier out of the setup so it would be something like: Asus Xonar Essence STX soundcard --> optical/SPDIF connection-->   DAC--> XLR-connection/splitter -->  2   speakers and a subwoofer.

I have run the command, this is the link that was provided:
[http://www.alsa-project.org/db/?f=31ce96da4225e328f8c838d136a5218fde6dc7ab](http://www.alsa-project.org/db/?f=31ce96da4225e328f8c838d136a5218fde6dc7ab)

---

### Post by Murderlove on 2010-07-11
Bump.

---

