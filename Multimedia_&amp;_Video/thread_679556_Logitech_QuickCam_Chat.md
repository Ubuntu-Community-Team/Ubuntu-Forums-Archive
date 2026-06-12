---
title: "Logitech QuickCam Chat"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by AAM on 2008-01-27
Webcam    Logitech QuickCam Chat
Lsusb        046d:092e Logitech, Inc.
Ubuntu      Gutsy 7.10
Kernel       2.6.22-14-generic

Installation HowTo
[LIST=1]
[*]** sudo apt-get install gspca-source**
[*]Plug in your webcam.
[*]**sudo gedit /etc/rc.local**[LIST=1]
[*]add **chmod 777 /dev/video0 **on the line before **exit 0**[/LIST]
[*]**sudo gedit /etc/modprobe.d/options**[LIST=1]
[*]add **options gspca gamma=6 **at the end[/LIST]
[*]reboot your PC.
[*]Check camera is working with Camorama, Ekiga or VLC (enable streaming locally for **/dev/video0**[/LIST]   	    The colours are less than vibrant!

---

### Post by bwtranch on 2008-01-27
That camorama thing crashed my usb printer. it messed up my USB and I had to install Gutsy to fix it..

---

### Post by bwtranch on 2008-01-27
Actually I had to fix it myself. But, the new kernal helped. That driver is garbage and I recommend compiling one yourself. This may sound hard, be it really isn't. Gentoo web site can help.

Webcams need to be compiled in the kernal and not as a module. This is where the trouble starts. Conflicts occur between the module and the kernal. No amount of dinking around with the files can fix this. I know, I've already tried. Now you can get a webcam that will work, out of the box. Guess what? it's 1000 + . Well, that's out of my price range.

---

### Post by AAM on 2008-01-27
I tried Camorama, but it was very unhelpful. Ekiga showed the image without configuration.

---

