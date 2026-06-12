---
title: "No Sound, all Eld=0"
date: 2011-05-26
forum: Multimedia Software
---

### Post by VicenteAtl on 2011-05-26
Hi, I have just installed Ubuntu 11.04 and can't get no sound. My card is recognized. Checking other post I have typed 

grep eld_valid /proc/asound/NVidia/eld*
/proc/asound/NVidia/eld#0.0:eld_valid        0
/proc/asound/NVidia/eld#1.0:eld_valid        0
/proc/asound/NVidia/eld#2.0:eld_valid        0
/proc/asound/NVidia/eld#3.0:eld_valid        0


so no eld is =1.  So I have re installed alsa and there is no solution. Also I have manually check sound with 
aplay -D plughw:NVidia,9 /usr/share/sounds/alsa/Front_Center.wav

and no sound.

I would be very gratefull is some one could help me with this
Thanks

---

### Post by VicenteAtl on 2011-05-31
These are more outputs to see if any can guess the solution. It's really bad not having sound!

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by lidex on 2011-05-31
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by VicenteAtl on 2011-05-31
Thanks for helping!

[http://www.alsa-project.org/db/?f=50bd389b4715867586c89faf63f1b87941e9286e](http://www.alsa-project.org/db/?f=50bd389b4715867586c89faf63f1b87941e9286e)

---

### Post by lidex on 2011-06-01
I see you're using the pae kernel. It seems to be causing some audio issues. Try booting into a non-pae kernel.

---

### Post by VicenteAtl on 2011-06-01
In the liveCD version of 64 bits I can't have sound either (I prefer to check it before installing that version, even though I should do it anyway).So  I created the new alsa information running from the 64 bits CD 


[http://www.alsa-project.org/db/?f=c35fdcbee05a89160ac4ad9e7bbb10b11f6234fd](http://www.alsa-project.org/db/?f=c35fdcbee05a89160ac4ad9e7bbb10b11f6234fd)

---

### Post by VicenteAtl on 2011-06-02
I solved it. Installling the 64 bits version and modifying the alsa.conf file

---

