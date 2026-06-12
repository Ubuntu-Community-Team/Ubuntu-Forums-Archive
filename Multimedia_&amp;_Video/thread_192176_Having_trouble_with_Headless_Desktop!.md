---
title: "Having trouble with Headless Desktop!"
date: 2006-06-08
forum: Multimedia &amp; Video
---

### Post by BlitzSonik on 2006-06-08
Hello, Windows admini here looking to learn Linux.  So far so good!

I have a desktop computer that I use as a file server.  It used to have Windows on it and I would remote desktop (or VNC) into it to do what I needed to do (audio and video conversion, file sharing, etc.).  When I started learning more about Linux I decided to wipe it clean and install Ubunut Breezy (all I had at the time).  I have since upgraded it (via apt-get dist-upgrade) and I have the GNOME desktop installed.  

My goal is to set this computer up so that I can set it in a corner (or closet) with nothing but a power cord and network connection plugged in.  So, with a monitor, keyboard, and mouse attached, I configured VNC to accept incomming connections with no confirmation required and a password, oh and to autologin as well.  This configuration worked beautifully...until I took the monitor off.  When the machine came back up (after I powered down to move it into the closet) I could connect to it fine but the screen resolution was set at 640 X 400 with no other options available.  This causes obvious headaches as when I connect via VNC, I get a very small, almost unworkable screen.  This only happens when the monitor is not attached as when it was, I had all kinds of resolution and freqency options and the resulting display on VNC was normal.

My question is this:  How can I configure the desktop so that it will use a preset resolution regardless if a monitor is attached or not.  For simple administration and file sharing, I know I can use SSH but in some cases I will need like a gui as I am assuming most of the apps that I will be testing/using will require one (i.g. audio and video conversion).

I would really like to figure this out as I really like Ubuntu and would rather not have to switch back to Windows.  Also, anybody know of any good audio and/or video conversion tools for Linux out there.  I am sure to find some on SourceForge but I haven't looked yet.

Thanks for any help I can get.

Blitz

---

### Post by pedwards on 2006-06-08
your problem is very easily solved,
you dont need to have gnome installed on your server to be able to access it through ssh on another computer, 
what you could do is un-install the desktop, and just run a ssh server on your closet pc. so when you login to it remotley, you will still see everything gui style,

to uninstall gnome desktop simply do,
sudo apt-get remove ubuntu-desktop
    and if you feel you need to get it back, simply do 
sudo apt-get install ubuntu-desktop

good luck!

---

### Post by BlitzSonik on 2006-06-08
[QUOTE=pedwards]your problem is very easily solved,
you dont need to have gnome installed on your server to be able to access it through ssh on another computer, 
what you could do is un-install the desktop, and just run a ssh server on your closet pc. so when you login to it remotley, you will still see everything gui style,

to uninstall gnome desktop simply do,
sudo apt-get remove ubuntu-desktop
    and if you feel you need to get it back, simply do 
sudo apt-get install ubuntu-desktop

good luck![/QUOTE]

I get that I can use SSH for CLI stuff.  But I want to be able to view the desktop gui via VNC from a Windows machine.

---

