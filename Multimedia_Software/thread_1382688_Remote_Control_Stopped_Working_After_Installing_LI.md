---
title: "Remote Control Stopped Working After Installing LIRC"
date: 2010-01-16
forum: Multimedia Software
---

### Post by munchkinmunchkin on 2010-01-16
I have a Medion RF Remote control with matching USB RF receiver, when I plugged it in, most of the buttons worked although some functions were on the wrong buttons.

I remember seeing 'Infrared Remote Control' in the Ubuntu software centre, so I installed it without success, as the remote completely stopped working with LIRC installed, can't even detect the RF receiver which was working fine before I installed LIRC.

I've tried many configurations without success and in the end I completely removed LIRC and the other packages that were installed with it.

Does anyone know how to get the original non-LIRC remote control configuration back?

I'm using 9.10 64bit

---

### Post by IcarusR on 2010-01-17
Check in /etc/modprobe.d/blacklist to see if any obvious median modules have been added (blacklisted) by the lirc install.

---

### Post by sports.car.guy on 2010-01-17
It sounds like when you installed Lirc you are now having to deal with no configuration files for any programs to use with the remote.

Go to ~/.lirc and see if there is any text files in there setup with key bindings in them and let us know from there.

---

### Post by ebygnome on 2010-01-20
I have just had the same problem. Installing lirc caused the remote to stop working !

So have removed it with a sudo apt-get remove lirc , and now the remote works again.

---

### Post by sports.car.guy on 2010-01-20
I see why you are having issues now. You installed Lirc which is now in charge of the receiving of the remotes key presses. You need to now tell Lirc what your remote is. Your remote being RF should not be a problem either. Lirc can work with them.

They should rename it to just Linux Remote Control or something to end some confusion.

If you have Gnome or Mythbuntu, both provide the ability to choose the actual remote you have. In Gnome there is an application on the repositories to configure the remote. It lets you choose the module and test it. In the testing it will let you get all of the codes off of the remote for each key, like a name if one of the standard ones, or hex code if not. 

You can then take the names of each button, or the hex depending, and use it to now assign the keyboard shortcut of an application to a button on the remote.  Each application that is Lirc aware usually looks for a file using it's name in ~/.lirc

Writing one of those files is easy. The Mythbuntu application won't show you each key name, but it generates several Lirc profiles for media players like MPlayer and VLC.

There is a lot of documentation on writing these files as well online. Mythtv has a great example for it on their website and I believe maybe for MPlayer and VLC as well.

I hope this helps.

---

