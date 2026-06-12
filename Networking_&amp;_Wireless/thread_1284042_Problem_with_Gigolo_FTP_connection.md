---
title: "Problem with Gigolo FTP connection"
date: 2009-10-06
forum: Networking &amp; Wireless
---

### Post by crantok on 2009-10-06
Hi Ubuntu forums. First Post. I was a C++ programmer working on and for Windows for many years. I recently started developing websites in Drupal and decided to switch to Xubuntu. I've really come to like Xubuntu and am now using it 90% of the time instead of Windows.

I was using Notepad++ (with its built in FTP feature) on Windows to directly modify files on websites. On Xubuntu, I'm using Geany and gFtp. This is more cumbersome and I would like to use Gigolo to make an FTP connection available to Geany. I have had mixed success with this.

I set up a bookmark in Gigolo to an FTP server and connected to it. In Geany, in the File -> Open dialog, I can see the FTP connection listed in the Places on the left hand side. By clicking on the FTP connection I can navigate its directory structure BUT when I select a file and try to open it, the dialog closes but nothing else happens; no file is opened in Geany and no line appears in its status display to say that anything happened.

Here's a list of things that I've noticed or that answer questions asked on the web in attempts to solve problems that I assume are related:

In the bottom left of the Geany's File -> Open dialog is a textbox that normally shows the selected file or directory. This is not updated as I navigate the directories on the FTP server.

In Mousepad, the File -> Open dialog does not show the FTP connection at all.

Trying to view the contents of the FTP server by choosing Actions -> Open in Gigolo, gives the following output:
gvfs-open: [ftp://(myUsername)@(mySite)/:]("ftp://%28myUsername%29@%28mySite%29/:") error opening location: No application is registered as handling this file

~/.gvfs already existed when I looked for it, but is empty.

I made my user a member of the fuse group (which already existed).

modprobe fuse, gives the following output:
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
FATAL: Module fuse not found.

According to /boot/grub/menu.lst, the kernel I am using is
     Ubuntu 9.04, kernel 2.6.30-02063003-generic
I changed the Kernel version while trying to improve the performance of my motherboard-integrated Intel graphics.

I'm sorry if the answer is staring me in the face. I'm happy to dig in to the guts of my system but I'm still fairly ignorant about how to do that on Linux.

---

### Post by crantok on 2009-10-09
Problem solved. I can now navigate FTP connections in Thunar (either by navigating to ~/.gvfs or by choosing "Open" in Gigolo) and open files through Geany's  File -> Open dialog.

One of the two following things fixed the problem but I didn't test in between:


[LIST=1]
[*]Implemented the network browsing how-to at [http://ubuntuforums.org/showthread.php?t=304131](http://ubuntuforums.org/showthread.php?t=304131)
[*]Installed gvfs-fuse using apt-get. I assume this is more likely to be the fix. I thought I'd already done it but was paranoidly rechecking that I'd done everything at [http://www.uvena.de/gigolo/help.html#id7](http://www.uvena.de/gigolo/help.html#id7)
[/LIST]

---

