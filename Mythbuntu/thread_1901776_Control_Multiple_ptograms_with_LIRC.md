---
title: "Control Multiple ptograms with LIRC"
date: 2011-12-29
forum: Mythbuntu
---

### Post by Mr.Si on 2011-12-29
Hi all,

I have my Mythbuntu setup and it is working nicely except the volume control in MythTV does not alter the output volume of the computer's sound card.

Is there a way to get LIRC to control a different "Prog" for different buttons on the IR remote?

Currently, everything controls the Prog of "MythTV".

Thanks,
Simon

---

### Post by klc5555 on 2011-12-29
You seem to be describing two unrelated issues. Usually when the volume doesn't appear to be controllable from mythtv, the issue is in the "audio" section of the frontend's setup menu. When your audio output and mixer devices are set to something along the lines of "Alsa:default", and when you have the box "use internal volume controls" checked, under "Mixer controls" you should have the options of PCM or Master. Usually PCM is the correct choice, but some installations may require you control the Master Mixer volume instead.

The lirc utility runs as a daemon independent of mythtv. Once running and configured for a particular IR remote, lirc can control any installed program as well as that other program is designed to be controlled by that particular IR remote. Some programs, like XBMC or Huludesktop are frequently added as executable menu items in mythfrontend and run from there, making mythfrontend essentially a fancy app launcher. But lirc and your configured remote should work normally with other programs if no component of mythtv is running at all.

---

### Post by Mr.Si on 2011-12-29
Thank you, I shall have a look at those tonight when I am home. (I'd look at it now, but my wife is watching Glee on the Frontend/Backend machine.

Si

---

