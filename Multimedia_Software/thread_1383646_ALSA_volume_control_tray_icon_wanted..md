---
title: "ALSA volume control tray icon wanted."
date: 2010-01-17
forum: Multimedia Software
---

### Post by josamoto on 2010-01-17
Hi guys! I had to remove Pulse Audio to get my sound working in X-Plane. After installing ALSA, sounds perfect, no complaints.

One side effect is that now my Logitech keyboard volume controls don't work, and I no longer have that nifty tray icon. Can I fix this, and install a tray icon for ALSA?

Also my Sound link says, "waiting for sound to respond" when clicking System>Preferences>Sound, can I fix/remove this?

---

### Post by sports.car.guy on 2010-01-17
You could have had both pulseaudio and alsa coexisting. You do not need to have one or the other. Reinstall your pulse audio if you want it, personally I haven't found it to be needed, then sound should come back up. It is looking for pulseaudio even though it is not on your system anymore. If you are using straight Ubuntu it has been designed to used pulse primarilly. Kubuntu does not have that issues.

---

### Post by gradinaruvasile on 2010-01-17
That tray icon is from PulseAudio. It replaces the old one that was sound system agnostic. There isnt an icon for ALSA anymore. Alsamixer in terminal or the graphic version of it is available though.
Also the sound link you are talking about was changed too. It was pointing to the same sound preferences you got from the PulseAudio tray icon.

---

### Post by FLOZz on 2010-10-21
I'm working on a python script for controlling the ALSA volume with a systray icon

[https://launchpad.net/alsa-tray](https://launchpad.net/alsa-tray)

The script does not support the multimedia key yet, but I will code it soon

if you want to install it :
```
sudo add-apt-repository ppa:flozz/flozz
sudo apt-get update
sudo apt-get install alsa-tray
```:)

---

### Post by Yellow Pasque on 2010-10-21
The issue is already solved with: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

---

