---
title: "linux, and remote desktop"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by hedoe on 2009-11-12
does anyone know if the remote desktop is possible with Ubuntu or DSL?

---

### Post by cgb on 2009-11-12
You can use Terminal Server Client to connect to Windows Remote Desktop within Ubuntu.  Not sure if this is what you meant.  If you are trying to setup a remote desktop server within Ubuntu then you can either use vino which comes with Ubuntu and can be enabled under System/Preferences/Remote Desktop or you can try another application such as NX-server for this task.  I prefer NX-Server myself and it does a very good job.

---

### Post by doas777 on 2009-11-12
just FYI,
there are some remote control protocols for ubuntu, that are safe to connnect to the internet, but what ubuntu calls "remote desktop" is **not** safe to expose to the web.

look into freenx if you are looking for a safe way to connect graphically over teh internet.

---

### Post by hedoe on 2009-11-12
okay well what i was wanting to do
is to make a small box with Ubuntu installed
and have it be a download box of sorts
along with some other features that i havent decided on yet

so im looking for something to be able to log-in and then tell that Ubuntu based pc what to do
then go to bed and just let it run while im snoozing :D

thanks for the replys guys

---

### Post by doas777 on 2009-11-12
is this box on your network, or across teh internet somewhere?
if it is on your network, then it is safe to just use the "remote desktop" options under system -> preferences. you can connect to it in ubuntu in Applications -> Internet -> Remote Desktop Viewer, or in windows, download a vnc client like tightvnc or realvnc.

if you are connecting over the internet, you can use freenx. here is a tutorial:
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

you can connect with either linux or windows using the client software from [http://www.nomachine.com/](http://www.nomachine.com/)

---

### Post by hedoe on 2009-11-12
okay im using W7 atm, and i want a machine that i can connect to running Ubuntu
and then when im connected i want to be able to run that machine
like using FF or even as a bit-torrent machine
what would you do?

thanks again

---

### Post by cgb on 2009-11-12
Just some additional info in case your interested is that if you are mainly trying to just create a box for downloading torrents and such you could even setup Transmission, or probably other BitTorrent apps as well, to automatically add torrents that are placed in a folder.  So then you could technically just share a folder on your new box and throw the torrent files into this shared folder from your other networked computers without even having to login.

regarding your response above, either the built in Remote Desktop app or FreeNX should be able to work with Windows7 although I haven't tested either on Windows7.  The built in remote desktop would be the easiest to test and you would just need to load one of the free vnc viewer's on Windows7 which i'm sure there has to be one out there already for it.

---

### Post by jsfour on 2009-11-12
I actually am having problems with FreeNX refreshing on my client computer. When I minimize the FreeNX windows client (or bring a window over the client window) it comes back up all messed up. From what I read this is a Gnome problem. My solution is to reload all of the gnome panels per by running this command.
> killall gnome-panel nautilus 

Does anyone know of a better way to do this?

---

### Post by hedoe on 2009-11-12
load a free VNC viewer?
okay this is why im here, to learn
like what?

im running Windows 7 Home Premium 64-bit
can you give me a link or any guidance is greatly appreciated thanks :D

---

### Post by cgb on 2009-11-12
I'm not entirely sure what all is supported by Windows7 since I am not currently running it on any of my machines.  You could try the free version of realVNC, [http://www.realvnc.com/products/free/4.1/download.html](http://www.realvnc.com/products/free/4.1/download.html) .   Aside from that you will also need to enable the remote desktop server on the Ubuntu box by going to System/Preferences/Remote Desktop.

---

### Post by hedoe on 2009-11-12
thank you very much :D

---

