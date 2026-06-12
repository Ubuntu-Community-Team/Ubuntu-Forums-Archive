---
title: "Tascam US 122l (external audio interface) not working"
date: 2011-02-18
forum: Multimedia Software
---

### Post by Wild-Storm on 2011-02-18
Hi guys,
I own a Tascam US 122l USB audio interface. I just figured out how to run this thing with jack. Unfortunately the (output) sound is very very choppy and I am not able to use the volume control at all.
do you have any ideas on how i could fix that?
Or is there maybe a way to use my interface without jack and directly through alsa?

edit://
I used this how to: [http://www.premiumorange.com/la-page-web-of-phil/index.php?page=P030201](http://www.premiumorange.com/la-page-web-of-phil/index.php?page=P030201)

---

### Post by turiontzukosson on 2011-02-18
What is the output of aplay -l?

edit: This tutorial you mentioned doesn't work for me :( But for some even other reason, it seems.

---

### Post by Wild-Storm on 2011-02-18
aplay -l doesn't list the device:
```
mrnice@root:~$ aplay -l
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: Intel [HDA Intel], Gerät 0: ALC889A Analog [ALC889A Analog]
  Sub-Geräte: 0/1
  Sub-Gerät #0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 1: ALC889A Digital [ALC889A Digital]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0

```
alsamixer does recognize the device though, but it does not appear in the gnome sound settings neither in pavucontrol.
the card is listed in /proc/asound/cards.

btw user.log says this:
```
Feb 18 18:17:08 root pulseaudio[6084]: module-alsa-card.c: Failed to find a working profile.
Feb 18 18:17:08 root pulseaudio[6084]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="usb-TASCAM_US-122L_no_serial_number-01-US122L" card_name="alsa_card.usb-TASCAM_US-122L_no_serial_number-01-US122L" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.

```

---

### Post by turiontzukosson on 2011-02-18
Similar with me: aplay -l does not list my tascam.

Does aplay -MDusb_stream:1 -fS24_3LE -r44100 -c2 -twav --period-size=640 ~/test.wav or with appropriate settings work for you?

edit: Thanks for the JACK hint, it works for me now, too.
edit: The reason why KMixer and the gnome mixer don't show the tascam might be simply because all the volume settings can only be done virtually by hand on the tascam itself.

---

### Post by Wild-Storm on 2011-02-18
nope, aplay says: device not found

---

### Post by turiontzukosson on 2011-02-18
So what sound card settings did you feed into JACK in order to make it run?

---

### Post by Wild-Storm on 2011-02-18
i downlaoded asoundrc, restarted alsa, killed pulseaudio and wrote usb_stream:1 into the interface field

---

