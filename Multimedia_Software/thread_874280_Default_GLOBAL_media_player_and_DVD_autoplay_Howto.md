---
title: "Default GLOBAL media player and DVD autoplay Howto."
date: 2008-07-29
forum: Multimedia Software
---

### Post by ozfalcon on 2008-07-29
Hopefully this howto is of use to some people. If not entirely correct or the "right way" to do this.

Ok, 1st up:
Ubuntu really needs a GUI to make all this more sane. I am infact surprised at the lack of GUI config tools shipped with Hardy. Specifically tools for Passwordless logins, Default Multimedia options, Desktop icons and other small things. Use of gconf-editor is not sane.

This howto works for me (YMMV), Exchange whatever media player you prefer.
The aim is to replace totem as the default media player with mplayer for standard media files and xine for dvd/vcd files.

Now, Lets start: (Copy/paste Tomboy notes :))

GLOBAL:
Edit /etc/gnome/defaults.list
change totem to mplayer for all associated content

Find and change the following:
x-content/video-dvd=xine-dvd.desktop
x-content/video-vcd=xine-vcd.desktop
x-content/video-svcd=xine-vcd.desktop
x-content/video-blueray=xine-dvd.desktop
x-content/video-hddvd=xine-dvd.desktop

------------------------------------------------------------------------------------------------------------------------------

Change DVD from /dev/dvd3 to /dev/dvd by default (Fix xine /dev/dvd default problem)
see: [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/223534](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/223534)

sudo mv /etc/udev/rules.d/70-persistent-cd.rules /etc/udev/rules.d/70-persistent-cd.rules.disable
Reboot(?) to activate


copy xine.desktop to xine-dvd.desktop and xine-vcd.desktop

sudo cp /usr/share/xine/desktop/xine.desktop /usr/share/xine/desktop/xine-dvd.desktop
sudo cp /usr/share/xine/desktop/xine.desktop /usr/share/xine/desktop/xine-vcd.desktop

edit xine-dvd.desktop
Name=xine-dvd
Exec=xine dvd:/

edit xine-vcd.desktop
Name=xine-vcd
Exec=xine vcd:/

Make links for dvd and vcd:
sudo ln -s ../xine/desktop/xine-vcd.desktop /usr/share/applications/
sudo ln -s ../xine/desktop/xine-dvd.desktop /usr/share/applications/


Finished.


*NOTES*
When the dvd is autorun, The device location is passed as a FILE to the xine.desktop file (Which dictates how xine is run).
However we do not want to run xine like this. We want to run xine with dvd:/ or vcd:/ options to get full menu support.
ie.
file:///media/cdrom0	--->	xine-dvd.desktop (Ignore and access dvd instead)	---> run xine dvd:/

We want a separate xine-dvd.desktop file, So when we access other media (right click play with xine) xine acts normally.

---

### Post by canadiandude007 on 2009-11-28
Thanks very much for this!

This removed lots of jerky DVD playback by using Xine instead of Totem and now it defaults to that.

---

