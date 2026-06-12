---
title: "switch volume control to usb-headphones when plugged in"
date: 2011-09-01
forum: Multimedia Software
---

### Post by vipers36 on 2011-09-01
Hi,

I have a usb-headset and the sound works fine under natty.
But the volume buttons and the system tray volume control don't control the volume of the headset, but of the integrated speakers (which play no sound)

I tried to change my usb soundcard to default by adding 
options snd slots=,snd-usb-audio

to /etc/modprobe.d/sound.conf.

cat /proc/asound/cards gives me:
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf3a20000 irq 46
 1 [Headset        ]: USB-Audio - Logitech USB Headset
                      Logitech Logitech USB Headset at usb-0000:00:1d.0-1.2, full speed
29 [ThinkPadEC     ]: ThinkPad EC - ThinkPad Console Audio Control
                      ThinkPad Console Audio Control at EC reg 0x30, fw unknown



Thanks for any help!

---

