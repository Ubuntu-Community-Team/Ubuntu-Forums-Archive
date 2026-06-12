---
title: "HOW TO: fix splash/login window resolution/artwork"
date: 2008-03-18
forum: Multimedia &amp; Video
---

### Post by n-alexander on 2008-03-18
It is assumed that screen resolution and DPI already work while logged in. Otherwise fix /etc/X11/xorg.conf first. If it works while in session, but splash and/or login window are screwed up, or you just want to fix the artwork, then follow hints below.

1) sudo gedit /boot/grub/menu.lst

add vga=792 (1024x768):

kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f622900b-4696-46a4-8384-f3e07c772aa7 ro quiet splash **vga=792**

Google for vga=792 for other resolutions. **This should fix login window resolution.**

2) in Login Window (System/Configuration/Login window in GNOME?), Security tab, Configure X Server: add -dpi 96 to command

/usr/bin/X -br -audit 0** -dpi 96**
[B]
This should fix login window font size[/B].

3) in Login Window, Local tab, fix background color as necessary (initially brown)

4) sudo gedit /etc/gdm/PreSession/Default: on line 61 fix background color yet again:

# Default value
if [ "x$BACKCOLOR" = "x" ]; then
**BACKCOLOR="#dab082"**

5) login window artwork is directly editable with text editor and Gimp in /usr/share/gdm/themes, no compilation required. Copy an existing theme directory and work from it.

6) fix splash window  artwork. Splash screen needs to be compiled and installed.

the hard way: [http://news.softpedia.com/news/Change-Ubuntu-Bootsplash-Theme-55237.shtml](http://news.softpedia.com/news/Change-Ubuntu-Bootsplash-Theme-55237.shtml)

an easier way: 
install gcc, libbogl-dev, usplash-dev
download a pre-made splash theme from [http://ubuntu-art.org](http://ubuntu-art.org), pick up one with sources, and modify the artwork before compiling/installing

---

### Post by K.Mandla on 2008-03-18
Moved to Multimedia and Video.

---

### Post by maestrobwh1 on 2008-03-30
Minor issue, but the boot splash never works correctly on exit.  It just drops from the window manager (kde) to the console to log out.  There is some note about iotcl display something or other, but the machine shows the boot splash properly on boot... just not during shutdown.  Minor issue really but it would look nicer if it just showed up during shutdown.

---

