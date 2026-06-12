---
title: "XDVD Shrink Error"
date: 2009-10-21
forum: Multimedia Software
---

### Post by Whiteaker on 2009-10-21
Failed to execute child process "xdvdshrink.pl" (No such file or directory) when starting [LEFT][COLOR=red][FONT=serif]**_xdvd_**[/FONT][/COLOR][/LEFT]
 shrink

 I'm very new to ubuntu, but I followed these directions to install. I don't get it at all. Please Help I changed the directions to reflect dvdshrink-2.6.1-10mdk.src.rpm the current release on the website. Thanx in advance.

1. [Download the RPM from their website]("http://dvdshrink.sourceforge.net/").

2.  Get Alien

     Code:
     sudo apt-get install alien 
3. Convert RPM to deb

     Code:
     sudo alien dvdshrink-2.6.1-3mdk.noarch.rpm 
4. Install

     Code:
     sudo dpkg -i dvdshrink_2.6.1-4_all.deb 
5. Make menu item

     Code:
     sudo gedit /usr/share/applications/xdvdshrink.desktop 
then paste this into the file and save it..

     Code:
     [Desktop Entry]
Name=DVD Shrink
Comment=Make and shrink copies of DVDs
Exec=xdvdshrink.pl
Icon=/usr/share/[LEFT][COLOR=red][FONT=serif]**_pixmaps_**[/FONT][/COLOR][/LEFT]
/gnome-[LEFT][COLOR=red][FONT=serif]**_cd_**[/FONT][/COLOR][/LEFT]
.[LEFT][COLOR=red][FONT=serif]**_png_**[/FONT][/COLOR][/LEFT]
Terminal=false
Type=Application
Categories=Application;[LEFT][COLOR=red][FONT=serif]**_AudioVideo_**[/FONT][/COLOR][/LEFT]
;
[LEFT][COLOR=red][FONT=serif]**_StartupNotify_**[/FONT][/COLOR][/LEFT]
=true

---

