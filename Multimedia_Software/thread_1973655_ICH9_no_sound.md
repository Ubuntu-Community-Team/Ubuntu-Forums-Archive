---
title: "ICH9 no sound"
date: 2012-05-05
forum: Multimedia Software
---

### Post by cafebuzz on 2012-05-05
I recently formatted my hard drive.. 

I installed ubuntu 10.04. My sound doesn't work. I know that alsa says this one isn't compatible. I had the sound working before with this same computer. It's an HP G60 530us

I don't remember how I did it though and I'm having a lot of trouble finding the solution (i think i had to add something to alsa-base.conf but I really don't remember) 

aplay -l 
**** List of PLAYBACK Hardware Devices **** 
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]   Subdevices: 1/1   Subdevice #0: subdevice #0 
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]   Subdevices: 1/1   Subdevice #0: subdevice #0  

cat /proc/asound/card0/codec* | grep Codec 
Codec: Conexant CX20583 (Pebble HSF) 
Codec: Intel Cantiga HDMI  

I also tried doing this, but I get hung up on the last command: 
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa 
sudo apt-get update 
sudo apt-get install linux-alsa-driver-modules-$(uname -r) 

It says E: Couldn't find package linux-alsa-driver-modules-3.2.6  Any help would be appreciated..

---

### Post by cafebuzz on 2012-05-05
SOLVED

gedit /etc/modprobe.d/alsa-base.conf

add to the bottom:

options snd-hda-intel model=laptop
options snd-hda-intel position_fix=1 enable=yes

I don't understand why this works though.. so in the interest of learning would anyone like to tell me why this works?

---

