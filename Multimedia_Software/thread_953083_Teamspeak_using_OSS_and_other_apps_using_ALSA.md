---
title: "Teamspeak using OSS and other apps using ALSA"
date: 2008-10-19
forum: Multimedia Software
---

### Post by WarriorSl on 2008-10-19
Hi, i'm trying to use the teamspeak build found in the intrepid repo of ubuntu and it uses the OSS sound device, but when i run teamspeak, all other apps using alsa (firefox, amarok, etc.) stop working sound, says that the device isn't available, is there any way to run like OSS and ALSA at the same time? like i'm talking and hearing in teamspeak and listening to music in amarok?

---

### Post by markbuntu on 2008-10-20
It depends. If teamspeak is using OSS then you can try launching it with aoss which is the ALSA wrapper for OSS apps. This will supposedly make teamspeak think it is using OSS but it will actually be using ALSA. If your ALSA apps can share the sound device, this may let teamspeak work the same way. If you are using pulseaudio, you can try padsp which is the oss wrapper for pulseaudio. Just put aoss or padsp before the teamspeak command in the launcher.

---

### Post by MRiGnS on 2008-10-20
AOSS apparently stopped working with teamspeak in intrepid alltogether, and padsp isn't an option because the wrapper lacks full duplex support which leads to crackling sounds using your mic.

The only viable solution that works all the time is getting a cheap second sound card, maybe integrated in an usb headset.

---

### Post by markbuntu on 2008-10-21
USB headsets are a good option, maybe $10 more than a regular headset of the same quality. I have one that has plugs for the headest on the usb dongle so I can use my high quality headphones with it or plug the headset into my sound card.

USB devices are treated as totally separate devices by alsa and pulseaudio and oss, just like a second sound card.

---

### Post by EseNoy on 2009-06-09
Hi, I've found a "weird" solution with non-usb micro (with Ubuntu 9.04). 

I've installed the pulseaudio applet. Open the volume control in the applet and go to the recording tab; then open teamspeak an watch how many streams of audio TS2 created. If there is only one stream, teamspeak must work correctly, if not, terminate all the streams and restart teamspeak.

It works for me, but I don't know why... please tell me if you have the same issue.

Regards

---

