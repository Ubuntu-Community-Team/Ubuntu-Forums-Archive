---
title: "VLC Issue(s)"
date: 2006-12-12
forum: Multimedia &amp; Video
---

### Post by golem3 on 2006-12-12
I recently switched over from WinXP to Dapper Drake 6.06, and found that VLC was not as great on Ubuntu as is it on Windows.

For example, in Windows, I used to use VLC for EVERY file format. Now, VLC just plays files and non-CSS DVDs. I guess it doesn't matter since I can play any DVD with MPlayer...Does anyone know how to get VLC to be as good as the other lower end Ubuntu players? 

Second, VLC seems to want to play dvds with a command

dvd:// 

but the only way it will work with NON-encrypted (no CSS) is with a tweak that I thought of 

/dev/cdrom

Any hints on why this is so?

---

### Post by superm1 on 2006-12-12
You will need to install libdvdcss2.  Have you done this?
sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/install-css.sh

---

### Post by golem3 on 2006-12-12
Ya, superm1 - it's not that, I have all those files. 

I am talking about VLC the program pointing incorrectly to the DVD file.

---

### Post by superm1 on 2006-12-12
VLC pointing incorrectly to the DVD file.....
I am thinking you are meaning that when you try to open a disk in VLC, there is no device name by default.  If you have only one dvd drive, this will sometimes work to play dvds.  Other times you will have to put in /dev/dvd or /dev/cdrom or /dev/hda or /dev/hdc etc etc.  

My advice is to try launching vlc from a terminal.  When trying to open an encrypted dvd, a lot of output is produced on the terminal and will explain a lot about what the error its getting with trying to open the dvd.

---

