---
title: "No audio through headphones"
date: 2010-11-19
forum: Multimedia Software
---

### Post by Daniël Slenders on 2010-11-19
Hi

I have some problem with my sound settings. I only get sound through the internal speakers of my notebook, not through the headset.

Does anyone know how I can fix this?
My notebook is an Asus K52f with Ubuntu 10.10.


Daniël

---

### Post by gringo guy on 2010-12-29
Had a similar problem tonight with a 10.10 install using the alternate-i386.iso (had to use this due to the 3-year old "[Errno 5 Input/Output error]("https://bugs.launchpad.net/ubuntu/+bug/245794")" install bug). An install of 10.04.1 last week worked perfectly on a different PC -- both internal speakers and USB headphones with microphone were working great within 2 minutes. 

Tonight, although the USB headphone was recognised in the System-> Sound-> Preferences Hardware tab, only the internal audio adapter was showing up in both the Input and Output tabs. After googling forum posts, I tried installing the VLC media player, using the package manager, as this dragged along several pulse libs and plug-ins that were recommended (and I like this app anyway). Also, FWIW, earlier I had installed the "[*ubuntu*-*restricted*-extras]("https://help.ubuntu.com/community/RestrictedFormats")" bundle and the prerequisite libs for Skype.

Close, but no cigar: I then had to reboot to get the headphones to show up as selectable devices in the Input and Output tabs (logging out and back in was not enough). After selecting the new device and starting some music, the LED on the headphone cord was flashing like a signal was arriving, but still no sound. At this point I simply unplugged the USB cable and re-inserted it. Voilà! Sound. Then, after selecting the mic in the Input tab, a Skype test call worked as well.

---

### Post by lidex on 2010-12-29
This thread should help:
[http://ubuntuforums.org/showthread.php?t=1460790](http://ubuntuforums.org/showthread.php?t=1460790)

---

