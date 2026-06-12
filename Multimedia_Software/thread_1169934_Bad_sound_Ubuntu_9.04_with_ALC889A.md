---
title: "Bad sound Ubuntu 9.04 with ALC889A"
date: 2009-05-25
forum: Multimedia Software
---

### Post by ashtone on 2009-05-25
Ive post this in other thread which had some similarities to mine

I have a mainboard GA-MA790FX-DQ6 with an integrated sound card Realtek ACL889A which runs fine in windows XP

Ive installed a clean ubuntu 9.04 jaunty, when I play a video or a mp3 file, I cant hear the sound, instead I just get some kind of noise, just like the sound is playing too fast or too slow but worse than that

Ive followed several guides in order to get sound running fine but its seem impossible, Ive followed the guide of Psyke83 but it didnt work forme, also tried other guides and all combination of configuration Alsa, OSS, autodetect

Some one experimented that issue ?

I paste here the main commands for checking sound hard :
aplay -l :
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: SB [HDA ATI SB], dispositivo 0: ALC885 Analog [ALC885 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: SB [HDA ATI SB], dispositivo 1: ALC885 Digital [ALC885 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 2: HDMI [HDA ATI HDMI], dispositivo 3: ATI HDMI [ATI HDMI]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

ashtone@Cubash:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe024000 irq 16
 1 [Camera         ]: USB-Audio - Camera
                      Camera at usb-0000:00:13.0-2, full speed
 2 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfdefc000 irq 19

ashtone@Cubash:~$ cat /proc/asound/modules 
 0 snd_hda_intel
 1 snd_usb_audio
 2 snd_hda_intel

---

### Post by oliverthered on 2009-12-25
alsa changes the way that this card (or more specificly the model of the card) is detected.

I've written the attached scripts to go through all the possible model numbers, you'll need to change mpg321 to mpg123 if that's what you've got installed and change the path to the mp3 file. (or change it to something else to play different types of audio file)

models in models.txt are taken directly from the alsa source code.

NOTE: there's a bug in alsa and sometimes you may get a kernel fault, the module won't unload and you need to reboot.

also some models may seem to work, but not work fully so try them all and then maunally try the ones that work to find the best one. (only one model worked for me though)


This script needs to be run with nothing bound to the module so exit X and drop to console first (or boot to console)

---

