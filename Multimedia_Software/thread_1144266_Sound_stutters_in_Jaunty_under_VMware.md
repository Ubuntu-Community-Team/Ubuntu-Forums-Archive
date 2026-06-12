---
title: "Sound stutters in Jaunty under VMware"
date: 2009-04-30
forum: Multimedia Software
---

### Post by chris-at on 2009-04-30
I have a Kubuntu 9.04 guest running under VMware.

- when I use "Ensoniq AudioPCI" in "Multimedia System Settings the sound stutters
- when I select PulseAudio the sound won't work at all.

For testing I installed Ubuntu (Gnome) in another VM and there the sound works great if I select "OSS" in the Sound Preferences.

How can I do the same with KDE?

Thanks.

---

### Post by chris-at on 2009-05-04
Is there a better place to get an answer to this kind of question?

---

### Post by martamius on 2009-05-21
I had the same problem with really crappy audio in kubuntu running as a guest OS. The fix is to install pulseaudio as described in the linked page below.
[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)
Then after a reboot, under seystem settings-> media, move pulseAudio above the ensoniq AudioPCI device for all your outputs. Wala! working sound.

---

### Post by wolverine25 on 2010-03-03
I am under Karmic Koala, have exactly same problem, stuttering sound whatever the application used to read it. I have tried all you said, martamius, it didn't change anything !!
Sometimes it is showing up : Ensonic audio pci not working. Under audio media settings I moved pulse stuff above everywhere... Wala ! sound still not working !!!
When i start the pulse audio applet, output device is still ES1371 audio pci-97, the pulse audio sound server doesn't show in the list, but only this ES1371.
I have lost plenty of hours trying to solve this problem, now if the linux guys cannot program correctly for something as fundamental as the sound in a system working without all these manipulations (and in this case nothing works !), what about coming back to M$ ??

---

