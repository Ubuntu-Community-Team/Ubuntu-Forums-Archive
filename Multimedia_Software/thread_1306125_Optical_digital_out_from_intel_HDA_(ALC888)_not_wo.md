---
title: "Optical digital out from intel HDA (ALC888) not working"
date: 2009-10-30
forum: Multimedia Software
---

### Post by fjf on 2009-10-30
I've done all I can and do not find the answer.  I installed Karmic amd64 and gnome-alsamixer and found the digital out of my soundcard and ticked it and worked great.  After a reboot, all I see in gnome alsamixer is card=pulseaudio  Chip=pulseaudio.  And nothing to tick.  In Jaunty I found the choices in pavucontrol or within volume control of padevchooser.  Now it is empty, nothing to choose from.

head -n 1 /proc/asound/card0 gives back:  /codec*Codec: Realtek ALC888

 aplay -l gives back:  
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: ALC888 Analog [ALC888 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 1: ALC888 Digital [ALC888 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

All which is correct and worked fine in Jaunty.  Anything I can do to select the ALC888 digital as default sound output?.

Thanks!

---

### Post by fjf on 2009-10-30
I'll answer myself.  After another reboot I found gnome-alsamixer working again; I ticked again everything and got sound.  I hope it lasts this time!.

---

