---
title: "HOWTO: Alsaconf for Ubuntu!"
date: 2006-12-02
forum: Multimedia &amp; Video
---

### Post by thamarok on 2006-12-02
Hello!

As I'm a real Linux junkie, nothing is too hard for me :D 
So, I decided to build the alsa-utils (version 1.0.11) from source to have alsaconf :-k 

So, I made up this procedure which works winderfully:
> sudo apt-get install gettext dialog
wget http://backports.org/debian/pool/main/a/alsa-utils/alsa-utils_1.0.11.orig.tar.gz
tar xvzf alsa-utils_1.0.11.orig.tar.gz
cd alsa-utils-1.0.11
./configure
sudo make install

Ofcourse, you can build the newest alsa-utils package, but as I saw in packages.ubuntu.com, Edgy Eft uses 1.0.11 so I thought it would be good to build the same version.

If you follow the installation procedure above, you'll get alsaconf for your Ubuntu, and it works wonderfully here :mrgreen:

---

### Post by marmalade on 2007-01-08
:KS Nice one, thamarok...

I've always used the 'run alsaconf, press enter a few times' workaround to deal with the my laptop sound stopping working occasionally.
I upgrade to Edgy and find that the devs in their infinite wisdom have removed this helpful command. (The sound, as it seemingly has done on many distros for years still stops occasionally with no apparent logic, but I can live with this).

Your script worked a treat (though I needed to apt-get install libncurses5-dev) and saved me needing to devote brain capacity I just don't have at this time of day...

---

### Post by Pjotr123 on 2007-01-09
You can get the doubleclick-and-go package with Alsaconf, from Ubuntu Netherlands (thank you, Dennis!). 
This makes installing Alsaconf a real no-brainer!

Download it here:
Dapper Drake (6.06) version:
[http://seveas.ubuntulinux.nl/~dennis/alsa-utils_1.0.10-1ubuntu14seveas1_i386.deb](http://seveas.ubuntulinux.nl/~dennis/alsa-utils_1.0.10-1ubuntu14seveas1_i386.deb)

Edgy Eft (6.10) version:
[http://seveas.ubuntulinux.nl/~dennis/alsa-utils_1.0.11-6ubuntu2seveas1_i386.deb](http://seveas.ubuntulinux.nl/~dennis/alsa-utils_1.0.11-6ubuntu2seveas1_i386.deb)

The package is in .deb format, so it is self installing. Do it as root (type first "sudo nautilus" in the terminal, to start a graphical explorer with root rights).

After the installation, you can run Alsaconf by typing in the terminal: sudo alsaconf
Caveat: on old hardware, this may take a while, especially the building of the sound card database!

Ave, Pjotr.

---

### Post by fsman on 2007-01-09
any chance you can change the dependencies?
If you try to uninstall your deb you get dependency problems with GDM and gnome-contol-center - not good.

---

