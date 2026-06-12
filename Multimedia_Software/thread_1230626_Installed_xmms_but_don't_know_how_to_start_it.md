---
title: "Installed xmms but don't know how to start it"
date: 2009-08-03
forum: Multimedia Software
---

### Post by ron_jeremy on 2009-08-03
*** I'd like to point out this problem is happening on my Mint Linux (Jaunty) box. The forums over there are very quiet so I chanced some help here ***

I followed the steps [here]("http://www.pvv.ntnu.no/%7Eknuta/xmms/") to install xmms:

No problem adding the repositories:

deb [http://www.pvv.ntnu.no/~knuta/xmms/jaunty]("http://www.pvv.ntnu.no/%7Eknuta/xmms/jaunty") ./
deb-src [http://www.pvv.ntnu.no/~knuta/xmms/jaunty]("http://www.pvv.ntnu.no/%7Eknuta/xmms/jaunty") ./

No problem with the following:

aptitude install fakeroot
apt-get build-dep xmms
apt-get -b source xmms

dpkg -i xmms_1.2.11-1_i386.deb

However, I can't figure out how to start the program because it's not in the Menu list. I noticed my home folder has now been bombarded with xmms related stuff but I have double clicked pretty much every file in there to start xmms but to no avail.

[[IMG]http://i72.photobucket.com/albums/i181/thanasi67/th_home-xmms.png[/IMG]]("http://s72.photobucket.com/albums/i181/thanasi67/?action=view&current=home-xmms.png")


[[IMG]http://i72.photobucket.com/albums/i181/thanasi67/th_home.png[/IMG]]("http://s72.photobucket.com/albums/i181/thanasi67/?action=view&current=home.png")


Any suggestions?

---

### Post by mc4man on 2009-08-03
It should start off of the command xmms
For a quick test either open a terminal, type xmms, press enter or go Alt+F2 , type in xmms and click run (don't ck. the run in terminal box

If all is well then make a desktop launcher with the name and icon of your choosing, command of xmms

(if you wish to see the files that were installed and to where d. click on your .deb and look under included files tab.

I noticed that repo has a pre made .deb, if your built one is an issue remove it and use the repo's one.

(even though it's for jaunty the deb here installed cleanly on my hardy, 
[http://www.pvv.ntnu.no/~knuta/xmms/jaunty/](http://www.pvv.ntnu.no/~knuta/xmms/jaunty/)


Edit:
you could create a menu item if you wish and or a xmms.desktop file 

(( desktop launchers can be dragged onto the top or bottom panel for ease of use

---

### Post by ron_jeremy on 2009-08-03
Hi mc4man,

thanks for the help. I ran xmms in the terminal & it opens up! This is what I saw in the terminal:

ronjeremy@komp ~ $ xmms

Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
Message: device: default

I dunno what the warning means but xmms seems to be working. I also downloaded the file you linked to & will save that for another time.

Anyway, I'm having a problem not being able to adjust volume settings with the xmms volume slider. This is true regardless if I'm using my headphones (plugged into my computer) or if I output sound to my stereo via coax digital. I can get around it for headphone use by adjusting the "master" slider in volume control however I cannot see any way to adjust the volume that is output to the stereo, where 90% of music listening is done.

Any suggestions?

---

### Post by ron_jeremy on 2009-08-03
Oh, I forgot to mention the volume issue does not happen with the other Linux Mint default media players.

---

### Post by ron_jeremy on 2009-08-03
Nevermind I figured it out by fishing around the xmms settings & switching output from oss to alsa. Seems to be ok now!

---

