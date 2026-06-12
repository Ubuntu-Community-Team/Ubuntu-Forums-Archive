---
title: "HOWTO: Kubuntu XGL+Compiz on ATI"
date: 2006-09-22
forum: Multimedia &amp; Video
---

### Post by mrbrdo on 2006-09-22
This is a howto for installing XGL and Compiz (in simple words: 3D desktop) on Kubuntu (KDE) with ATI drivers.

First, if you haven't done so already, install the fglrx driver following this howto: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Now, check if your drivers are installed correctly.
Open a terminal and type:
```
glxinfo | grep OpenGL
```
Output should be similar to this (it's definetly not working if it mentions MESA):
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600 Generic
OpenGL version string: 1.2 (2.0.6011 (8.28.8))
```
NOTE: You might or might not have the first line. It does not matter if you do or do not.

In terminal, type:
```
glxinfo | grep direct
```
Output should say:
```
direct rendering: Yes
```
NOTE: After you will login to XGL, it will most probably say No. This is normal.

If the above commands don't display what they should, there is a problem. Things you can try to do to fix this (after doing each step, **reboot the machine** and see if it works yet):
1. In terminal, type "sudo nano -w /etc/X11/xorg.conf"
Under Section "Device", check that they all say Driver "fglrx". If they say "ati" or "radeon" or anything else, change it to "fglrx".
2. sudo nano -w /etc/X11/xorg.conf
My Section "Device" looks like this, see if you are missing any of the options:
```
Section "Device"
        Identifier  "ATI Card Name"
        BusID       "PCI:1:0:0"
[COLOR="Red"]        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
#        Option      "UseInternalAGPGART" "no" # check comments about[/COLOR] this line
EndSection

```
Uncomment the Option "UseInternalAGPGART" "no" line if you installed fglrx from Seveas repositories or ati.com. If you didn't or don't know, then leave it commented or don't add it.
3. On some cards it is necessary to disable Composite:
sudo nano -w /etc/X11/xorg.conf
At the very end add:
```
Section "Extensions"
   Option "Composite" "disable"
EndSection
```
4. Reboot after following the above steps.
5. If this still doesn't solve it, seek help on the forums. Provide the output of "dmesg | grep fglrx", "dmesg | grep agp", your /etc/X11/xorg.conf and your /var/log/Xorg.0.log

Now, on to install XGL. There is a very good howto here: [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)
**IMPORTANT:** When you come to the part "Choose How Your Computer Will Start Xgl", be sure to follow Method A, as this howto will assume you have it set up this way.

Now that you've installed and configured XGL, try it out by choosing XGL session in the menu where you log in. It may be very slow, but as long as it's working it's ok. Log out, select KDE session again and continue:

Now we will install Compiz and CGWD, which are needed for a nice "3D desktop".
First, if you don't have the neccesary repository yet, you will have to add it. You have probably already added it when installing XGL, so you probably do not need to do it now.
If you don't have it yet, "sudo nano -w sources.list" and add this to the end:
```
# XGl and Compiz packages (packages)
deb http://media.blutkind.org/xgl dapper main
# XGl and Compiz packages MIRROR (packages) - if the first one doesn't work
#deb http://ubuntu.compiz.net dapper main
#deb http://www.beerorkid.com/compiz dapper main
```

Type in terminal:
```
sudo aptitude install compiz compiz-plugins csm cgwd cgwd-themes cgwd-themes-extra
```

You're almost done!
In terminal, run "sudo nano -w /usr/bin/startxgl.sh" (you should have made this script when you used Method A to configure XGL before) and add the lines written in red. I have included the whole content of the file just so you know where to put them, you do not need to change the part that is not written in red color.
```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
[COLOR="Red"]cgwd &
compiz &
xmodmap /usr/share/xmodmap/xmodmap.us # change us to your country name
#xmodmap -e "keysym comma = comma semicolon less" # uncomment this line if you want "AltGr + ," to produce "<" and it does not work
#xmodmap -e "keysym period = period colon greater" # uncomment this line if you want "AltGr + ." to produce ">" and it does not work
#xmodmap -e "keysym e = e E EuroSign" # uncomment this line if you want "AltGr + e" to produce "&#8364;" and it does not work[/COLOR]
exec startkde
```
I have included some xmodmap lines that fix a few key combinations that didn't work right for me in XGL. If you have another combination of keys that doesn't work in XGL for you, you can ask here how to make it work.
**IMPORTANT:** Please note that i didn't have the "/usr/share/xmodmap/" directory on my Kubuntu Dapper installation. It seems it is included in the "gnome-applets-data" package, but you do not have to install it - just ask a friend with Ubuntu installed to send the files to you. After you make the directory and put the files in, in case you didn't have it already, do "chown -R root:root /usr/share/xmodmap/" and "chmod 644 /usr/share/xmodmap/*".

Now, logout, change session to XGL in the menu, and log back in. If all went well you should now have a "3D desktop" :-)
If it doesn't work, first try to reboot and try to log in again, using XGL session.

Please post if this worked or did not work for you, and if you had to do anything besides what i wrote here.

**[COLOR="Red"][SIZE="3"]NOTE: THE COMPIZ REPOSITORIES (PACKAGES) MIGHT BE BROKEN AT THE TIME OF WRITING![/SIZE][/COLOR]**, which means you might not be able to install compiz, unless you manually download the packages (ask someone if you really want to do that). Otherwise wait until they are fixed.

---

### Post by DWRZ on 2007-08-15
I had XGL running on GNOME. I switched to KDE and had some trouble getting it working there, but I finally got it running thanks to your guide. However, I have noticed that XGL is running much more slowly than it was on GNOME. Any idea as to why, and if it is possible to fix this? I followed Method A.

Thanks again,
DWRZ

---

### Post by bggashnik on 2007-08-19
After I type in the console
```
glxinfo | grep OpenGL
```
the result is:
```
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.2
OpenGL extensions:

```
You said that if the result mension MESA it definitely won't work.Any suggestions How to get it work?I use Kubuntu faisty.Are the any howto-s about my  case?
P.S I can't spek very well English.Thanks in advance.

---

### Post by N3um0rin on 2008-06-05
Uhm..When i log onto xgl its all grey and it goes back to kde without loging out or anything..but its really slow..Can you help?

---

