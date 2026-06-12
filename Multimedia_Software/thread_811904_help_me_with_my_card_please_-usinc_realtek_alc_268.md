---
title: "help me with my card please -usinc realtek alc 268"
date: 2008-05-29
forum: Multimedia Software
---

### Post by kforum on 2008-05-29
ok im not sure if my card is working properly.

here is my aplay -l:
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

my lspci -v lists
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: COMPAL Electronics Inc Unknown device 0025
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at f8400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

as my audio hardware.
my cat /proc/asound/modules lists 0 snd_hda_intel.
and this is what i have in the end of /etc/modprobe.d/alsa-base

options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

shoudnt my driver be here? the snd-hda-intel or snd-intel8x0, assuming one of these 2 are the right ones...

basically my front(built in) mic doesnt work, or i cant get it to.
AND also, im not sure my sound is 100%, is it normal to have back noise? sometimes when i connect my headset to the laptop i hear static in the backgroun, its not too loud, but...

anyways compal says i have a:


10. Audio
	

-   Realtek ALC268

-   2 channel HD Audio

-   Compliant with Universal Audio Architecture

-   95dB SNR DACs / 90dB SNR ADCs can meet Vista Premium requirement

-   Microphone-in and headphone-out

-   Internal Microphone

-   Two stereo 1.5W speakers with chamber

-   Volume control: Hot-key control for Windows  


any clues or hints here would be greatly appreciated.
also, should i use pulseaudio instead of alsa?(im not even sure how to do that btw).
oh and the forums/the net doesnt really list aything to aid me here. :(

edit: also /proc/asound/pcm lists -> 

00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1
00-04: ALC268 Analog : ALC268 Analog : capture 1
00-00: ALC268 Analog : ALC268 Analog : playback 1 : capture 1

in case that matters.

---

### Post by kforum on 2008-05-30
noone has a clue?

---

### Post by kforum on 2008-06-01
btw if i try to use my headphone, i get tones of noise too.
that makes voip a nightmare.

---

### Post by davidkyn on 2008-06-01
Have you considered reinstalling?

---

### Post by kforum on 2008-06-02
i dont think its an installation issue everything seems fine and configured as far as i can tell.

maybe sound in linux is suposed to be like this?
i hope not...

anyways this is beyond my scope possibly, but... yeah reinstalling ubuntu, right now is not my idea of fun. =(

---

