---
title: "Sound on RPI5 with RPI-DAC Pro"
date: 2024-09-10
forum: Multimedia Software
---

### Post by yamigami2 on 2024-09-10
I am trying to get my RPI5 with an RPI-DAC-Pro to work. I cannot select it in the gui as it does not show. 

RPI 5 8g - Ubuntu 24.04.1 LTSy
RPI (IQAudio) RPI-DAC-PRO

If I drop to a terminal and execute the following:

grep -a . /proc/device-tree/hat/*


/proc/device-tree/hat/name:hat
/proc/device-tree/hat/product:Pi-DAC PRO
/proc/device-tree/hat/product_id:0x0008
/proc/device-tree/hat/product_ver:0x0003
/proc/device-tree/hat/uuid:f3d21f9f-64f4-4ee4-96aa-f779ea5cc2a9
/proc/device-tree/hat/vendor:IQaudIO Limited [www.iqaudio.com](www.iqaudio.com)

cat /proc/asound/cards
 0 [Pro            ]: RPi_DAC_Pro - RPi DAC Pro
                      RPi DAC Pro
 1 [vc4hdmi0       ]: vc4-hdmi - vc4-hdmi-0
                      vc4-hdmi-0
 2 [vc4hdmi1       ]: vc4-hdmi - vc4-hdmi-1
                      vc4-hdmi-1

It shows up.  I am not able to upload my system-info.txt yet but it shows no audio card.  The card works in LibreElec, Kodi, etc just not Ubuntu.

I will upload my system-info when I am able if needed. Is this an ALSA problem? I am not very good with that but am willing to dive in to make this work.

Any ideas?

---

