---
title: "HMDI audio for Radeon HD 5600 Series"
date: 2011-01-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by shakaran on 2011-01-15
Hi, I am using Natty for try enable HDMI audio with my Acer laptop (that have a Radeon HD 5600 graphic card) and LG 32" TV.

I get the video image on tv screen, but the sound don't work. I try before with Windows 7 and audio + video works perfectly.

When I try to enable HDMI audio sound on Sound Preferences, nothing happens.

I try launching the command gnome-volume-control and the same without errors.

I attach a couple of images of gnome-volume-control for hardware and ouput tabs (sorry about the spanish).

I thing that I have all the setting properly selected but it don't work. 

I read here: [http://ubuntuforums.org/showthread.php?t=1649527&page=5](http://ubuntuforums.org/showthread.php?t=1649527&page=5)

About put on gksudo gedit /etc/asound.conf
the line:
load-module module-alsa-sink device=hw:1,7

But this dont work for me and show the errors on gnome-volume-control:

```
gnome-volume-control

(gnome-volume-control:3797): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(gnome-volume-control:3797): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

** (gnome-volume-control:3797): WARNING **: Default sink stream not found

(gnome-volume-control:3797): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(gnome-volume-control:3797): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

```

Maybe I need some different hw:1,X line?

Some specs for the record:

```
$ aplay -l
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: ALC670 Analog [ALC670 Analog]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 1: ALC670 Digital [ALC670 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: Generic [HD-Audio Generic], dispositivo 3: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
```

```
$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]

```

```
$ uname -r
2.6.37-12-generic-pae
```

Could someone give me a hand with this? Thanks

---

### Post by efflandt on 2011-01-15
OK, I am just guessing because I have nvidia instead of ati (although I do have HDMI connected 32" LG HDTV) and do not understand your native language.  But since a device does show up in **aplay -l**, and if you get HDMI sound with **aplay -D plughw:1,3 /usr/share/sounds/alsa/Front_Center.wav** try removing /etc/asound.conf and insert a line after the alsa-sink line in /etc/pulse/default.pa:

```
#load-module module-alsa-sink
**load-module module-alsa-sink device=hw:1,3**
```Then after rebooting see what **Output** devices show up in **Sound Preferences**.  For mine it is actually the NVidia one that does NOT say HDMI (yours might be HD-Audio Generic).  It may work even if the speaker test in Sound Preferences does not work.  Try running Rythmbox or something and switching outputs in Sound Preferences.

---

