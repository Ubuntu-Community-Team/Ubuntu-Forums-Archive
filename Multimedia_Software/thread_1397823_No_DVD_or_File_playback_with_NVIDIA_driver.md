---
title: "No DVD or File playback with NVIDIA driver"
date: 2010-02-03
forum: Multimedia Software
---

### Post by Sean Brown on 2010-02-03
I have installed the recommended driver for my nvidia card (185), and after much fiddling finally got my config file to stick and boot correctly, however I can't see the output of the media player or the DVD player.  The files play because I can hear them, but I don't see any output.  I have moved the depth to 16 bit, but I still don't get anything.  Anyone else had this issue?

---

### Post by inobe on 2010-02-03
do you have **ubuntu-restricted-extras** installed ?


if not' go into synaptic, search and install.....

---

### Post by Sean Brown on 2010-02-04
I do have that package installed and I reinstalled it to be sure.  If I disable the nvidia driver it works fine, but the I lose widescreen resolutions.

---

### Post by kelvin spratt on 2010-02-04
It may help to post details of your Nvidia card
What player are you using VLC  works well but sometimes you need to change the vid playback settings to X11 or GL.
As for the Nvidia card you should not have any problems if you install through restricted extras and should not have to alter any files to keep the settings

---

