---
title: "How to Change the Resolution on Ubuntu Server"
date: 2008-01-30
forum: Multimedia &amp; Video
---

### Post by Eddymvp on 2008-01-30
I installed ubuntu server 7.10  and I can't read the text on my screen. I believe that my resolution is 640x400. I tried to change the resolution by editing the /etc/X11/xorg.conf file, but that file is not there since i'm running ubuntu server.
Can someone show me how I can change the screen resolution on ubuntu server? Thanks in advance for your help.

---

### Post by oedha on 2008-01-30
are you sure......the file wasn't there ???
do you have the gnome desktop or only terminal mode

open the file with sudo gedit /etc/X11/xorg.conf ( if you have gnome desktop )
or sudo nano /etc/X11/xorg.conf ( from terminal mode )

or reconfigure your xserver by
sudo dpkg-reconfigure xserver-xorg
or 
sudo dpkg-reconfigure -phigh xserver-xorg

regads;
~E~

---

### Post by xinix on 2008-01-30
You won't have that file since you are running a server install.   Try adding "vga=789"  (for 800x600) to the kernel parameters in /boot/grub/menu.lst or "vga=792" (for 1024x768 ).  And then of course reboot.

---

### Post by Eddymvp on 2008-01-30
> **oedha said:**
> are you sure......the file wasn't there ???
do you have the gnome desktop or only terminal mode

open the file with sudo gedit /etc/X11/xorg.conf ( if you have gnome desktop )
or sudo nano /etc/X11/xorg.conf ( from terminal mode )

or reconfigure your xserver by
sudo dpkg-reconfigure xserver-xorg
or 
sudo dpkg-reconfigure -phigh xserver-xorg

regads;
~E~


Thanks for your quick reply. I only have terminal mode and I don't have the gnome desktop installed.

I get the following error when I tried to configured the xserver.

$ sudo dpkg-reconfigure xserver-xorg
[sudo] password for:
Package `xserver-xorg' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-xorg is not installed

---

### Post by Eddymvp on 2008-01-30
> **xinix said:**
> You won't have that file since you are running a server install.   Try adding "vga=789"  (for 800x600) to the kernel parameters in /boot/grub/menu.lst or "vga=792" (for 1024x768 ).  And then of course reboot.


I tried adding vga=792, rebooted and the resolution still the same.

---

