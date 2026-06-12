---
title: "Alsamixer volumes not saved between reboots + audio settings for phonon not sticking"
date: 2011-07-21
forum: Multimedia Software
---

### Post by Oceanwatcher on 2011-07-21
Kubuntu 11.04
KDE 4.6.5

I have the same problem mentioned in various other posts - low volume on my Logitech headset.

Both my onboard sound and my Logitech headset works perfect. No problem with drivers or access.

And I am able to use alsamixer in the Konsole to fix the problem.

BUT - 

I have to do this EVERY time I reboot the computer.


Separate, but similar issue:
In the audio settings in KDE (System Settings>Multimedia>Phonon>Audio Capture>Communication) I am constantly seeing the microphone for the headset getting pushed down on the list so I have to bring it to the top again.

Does anyone have any idea how to make these settings stick?

---

### Post by lkjoel on 2011-07-21
> **Oceanwatcher said:**
> Kubuntu 11.04
KDE 4.6.5

I have the same problem mentioned in various other posts - low volume on my Logitech headset.

Both my onboard sound and my Logitech headset works perfect. No problem with drivers or access.

And I am able to use alsamixer in the Konsole to fix the problem.

BUT - 

I have to do this EVERY time I reboot the computer.


Separate, but similar issue:
In the audio settings in KDE (System Settings>Multimedia>Phonon>Audio Capture>Communication) I am constantly seeing the microphone for the headset getting pushed down on the list so I have to bring it to the top again.

Does anyone have any idea how to make these settings stick?
In a Terminal window, try:
```
sudo alsactl store 0

```
That should solve the problem with alsamixer.

---

### Post by SeijiSensei on 2011-07-22
> **Oceanwatcher said:**
> Kubuntu 11.04
KDE 4.6.5
In the audio settings in KDE (System Settings>Multimedia>Phonon>Audio Capture>Communication) I am constantly seeing the microphone for the headset getting pushed down on the list so I have to bring it to the top again.

This is a [known bug]("https://bugs.launchpad.net/ubuntu/+source/phonon/+bug/769274") in Kubuntu **11.04**; it's not a problem on my 10.10 installation, even with the [backports]("https://launchpad.net/~kubuntu-ppa/+archive/backports") repository (KDE 4.6.2) enabled.

---

