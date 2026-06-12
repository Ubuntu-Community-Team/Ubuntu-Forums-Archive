---
title: "why can't i play dvds?"
date: 2008-08-20
forum: Multimedia Software
---

### Post by Mzwo on 2008-08-20
no matter which player (totem, m-player, vlc) i use? restricted formats are installed, yet players keep crashing (totem), not finding streams (m-player) or not bothering to do anything (vlc). help?

thanks,
Mzwo

---

### Post by niyonk on 2008-08-20
Hi, before you installed any of those did you try something like...

-sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3
-sudo /usr/share/doc/libdvdread3/install-css.sh

If you have, then I do not see why it is not playing

OR 
Try the medibuntu way of enabling [DVD playback]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_DVD_Support")

---

### Post by Mzwo on 2008-08-21
hi,

i did not try any of the above, mainly because i don't really know my way round linux. as yet, in anycase. and i'm still slightly phobic of the commandline. any point in doing what you suggested after the install?

thanks,
Mzwo

---

### Post by niyonk on 2008-08-21
Hi, 

Although you had found your way to installing vlc, totem and others you might have not realised that those players will not include DvD playback as only the user will have to do that.

A DvD decoder is not included by default due to Legal stuff...:(
So, it will be up to the user to do it him/herself.

See [this page]("https://help.ubuntu.com/community/RestrictedFormats") for more

About the DvD problem you can see [this page]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs") to know what exactly the commands will do :)

Cheers! :biggrin:

---

### Post by Mzwo on 2008-08-27
thanks, mate. that did it.

Mzwo

---

