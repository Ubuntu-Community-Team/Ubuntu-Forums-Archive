---
title: "Sound issues with Amarok &amp; Kaffeine"
date: 2008-06-17
forum: Multimedia Software
---

### Post by gingermark on 2008-06-17
Hi there,

I have searched for solutions on this with no luck, but I have to assume they are out there, so apologies in advance. If someone could direct me to a relevant thread, that would be great.


I have done a fresh install of Hardy from the alt CD. Since then, I have used EnvyNG to install my nVidia driver, installed some upgrades (mainly security ones), installed the codecs as detailed in Part One of the "[Comprehensive Multimedia & Video How-to]("http://ubuntuforums.org/showthread.php?t=766683")" and downloaded the Medibuntu version of Amarok.

Everything seems to work fine, except I have no sound from Xine (so no sound from Amarok or Kaffeine). System sounds work fine, sounds from Firefox and Opera flash videos sounds fine.

I am assuming there is some problem between aRts and Xine. I haven't updated Kubuntu since Dapper - back then I could always restart the sound system and Amarok would then work.

I have tried to select ALSA both in the Xine engine options and in the Sound System options, but no luck.

I am desperate to get this to work - any help would be very much appreciated.

Many thanks.

---

### Post by gingermark on 2008-06-18
Ok, I managed to resolve this by editing the Xine engine options in both programs for ALSA output.

The stereo option for the Alsa Device Configuration was set at "plug:front:default". I have now changed this in both programs to just "default", and sound works great!

---

