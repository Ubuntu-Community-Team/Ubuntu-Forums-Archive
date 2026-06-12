---
title: "Cant choose Esound for freeNX audio support"
date: 2009-01-04
forum: Multimedia Software
---

### Post by Hemonator on 2009-01-04
Situation:
I got a desktop and a laptop, both running 8.10.
Freenx server is installed on desktop and client on laptop.
Remote-control works flawlessly.

It was hard for me to find any previous post of this anywhere, but i got one relatively small but comprehensive tutorial in [https://help.ubuntu.com/community/BroadcastAlertWithSound](https://help.ubuntu.com/community/BroadcastAlertWithSound).

Trick Should be simple: 
Enable multimedia on the client (done)                     
Install esound on the server (done)
Login via freenx and as a user on the server, choose esound from system -> pref -> sound -menu for everything possible (no can do!)

Problem:
There is no esd/esound/enlightement sound daemon/whatnot to choose from! There is Alsa, OSS, 2 options for ice1712 (oss) and one (alsa) and autodetect. No more no less.

More info:
ps -e | grep 'esd' shows that it is running. 
No difference if its started with root or user permissions.
esound is installed via "sudo apt-get install esound".
Pulseaudio is completely removed, every related package is removed, /etc/asound.conf deleted, removed the file from .../x.sessions and unticked from session startup list. 

It'd be superb if 
A. someone knew whats wrong with my setup and where the esd-option is hiding, or 
B. someone knew some other trick to make sound fly via freeNX. I have iced2 setup at the moment and amarok has a script to do ip-broadcastin itself, but im not satisfied with them for several reasons.

---

### Post by hugoheden on 2009-02-03
Hi, 

> Problem:
There is no esd/esound/enlightement sound daemon/whatnot to choose from! There is Alsa, OSS, 2 options for ice1712 (oss) and one (alsa) and autodetect. No more no less.

I had that same problem and solved it by installing the package gstreamer0.10-esd . 

That installs the file /usr/lib/gstreamer-0.10/libgstesd.so .. (the same one that NoMachine suggests to compile, see [http://www.nomachine.com/ar/view.php?ar_id=AR11E00491](http://www.nomachine.com/ar/view.php?ar_id=AR11E00491))

No need to log out/in or anything, just reopen that menu and the E-S-D option should be there.

I am running NoMachines nx-server and I get sound from those Test-buttons. And from mplayer.. But not from Flash in Firefox. Nor from VLC.. So if you want to cooperate further, please report back here :-)

Have you tried using the NoMachine nx-server? Did you get sound working properly?

Best regards

Hugo

---

