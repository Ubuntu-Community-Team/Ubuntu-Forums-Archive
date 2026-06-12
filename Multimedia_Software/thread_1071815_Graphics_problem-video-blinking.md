---
title: "Graphics problem-video-blinking"
date: 2009-02-16
forum: Multimedia Software
---

### Post by jahkob on 2009-02-16
Hi, i installed ubuntu 8.10 64bit. and now when i turn on the nice visual effects the films i play with vlc and movie player is blinking :-( 

i have a Ati Radeon HD 4830 and the fglrx driver installed.
it must be the driver... where can i get a better one, or can i?

Ati Radeon HD 4830 is a nice new card..
must get get a new one to watch movies :-( or must i go back to crapy windows...


stats:
Ubuntu 8.10 64bit
4G (800mhz) Ram, Ati Radeon HD 4830, AMD Atholn 64 x2 3Ghz.

sorry for bad english

---

### Post by johnno56 on 2009-02-16
Jahkob,

I have the same problem. I have just installed Ubuntu 8.10 32bit. The video blinks playing movies with VLC media player and Movie Player. It happens when playing DVD or AVI movies. My video card is Radeon HD 2400 Pro.

I have been using the same hardware when I was using Ubuntu 8.04 and it ran perfectly. I too am hoping for a "fix" or else I will have to go back to using 8.04

If I find out anything, I will let you know.

Regards

J

---

### Post by johnno56 on 2009-02-16
Jahkob,

Try the following:

On the top tool bar select "System".
Then select "Preferences".
Then select "Appearance"
Then select "Visual Effects"
Then select "NONE"
Then "CLOSE"

This will disable any fancy visual effects for the desktop, but this worked for me. I tested this with both VLC and Movie Player with DVD and AVI movies, and it worked like a charm.

This is not a solution but should get you by until a fix can be found.

Regards

J

---

### Post by johnno56 on 2009-02-17
Jahkob,

Another update:

The following modification seems to work for VLC and Movie Player even with the "EXTRA" visual effects activated.

First: Start up a "Terminal"

Top Menu Bar:
Select "Applications"
Select "Accessories"
Select "Terminal"

Enter the following commands: (case sensitive - Use capitals where indicated) - do NOT enter the text in the brackets ( )

cd /etc/X11      (capital X and the number eleven)
sudo cp xorg.conf xorg.conf_backup   (you will be asked for your password - this makes a copy of the file - just in case of mistakes)
sudo gedit xorg.conf   (This will edit the original xorg.conf file)

You should see, at the bottom of the file, something similar to below:

=================================================
Section "Monitor"
     Identifier "Configured Monitor"
EndSection

Section "Screen"
     Identifier "Default Screen"
     Monitor "Configured Monitor"
     Device "Configured Video Device"
     DefaultDepth 24
EndSection

Section "Module"
     Load "glx"
EndSection

Section "Device"
     Identifier "Configured Video Device"
     Driver "fglrx"
EndSection
==================================================

The section to focus on is the "Device" section.

Between Driver "fglrx" and EndSection  (your file may be slightly different), enter the following so that it looks like this...

Section "Device"
     Identifier "Configured Video Device"
     Driver "fglrx"
     Option "TexturedVideo" "off"
EndSection

Whatever info is in that section, the new line MUST be enter exactly as shown.

Save the file.

Exit all the way back to the Desktop, then reboot.

Try a DVD or AVI movie and let me know how you got on.

Regards

J

---

### Post by jahkob on 2009-02-17
johnno56 ty! it works!:D:D

---

### Post by binbash on 2009-02-17
set the video output to X11 at vlc's preferences

---

