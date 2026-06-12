---
title: "Mythtv works"
date: 2007-03-09
forum: Multimedia &amp; Video
---

### Post by Chuckels550 on 2007-03-09
This a note of appreciation to everyone who has contributed to the Ubuntu Mythtv documentation.  I finally got it to work  - and that is with the WinPVR 350 TV-out - and it was due to Ubuntu and its community documentation.  I tried using SuSE 10.0, 10.1, Fedora 5.0, and MythDora 3.1, 3.2.  I could not make it work using those distros.  So thanks!

Edgy Ubuntu 6.10
Slot 478, Intel P4 2.26 GHz, 533 MHz FSB
Asus P4S8X-MX mobo
Creative Labs Soundblaster Live 24 bit
Gigabyte Nvidia GeForce 6600 GT
Hauppauge WinTV PVR 350, model 990 (NTSC tuner) 
Dlink DWL-G520 High Speed 2.4GHz (802.11g) Wireless PCI Adapter, Rev B

---

### Post by tagra123 on 2007-03-09
Enjoy.

Some good advice now that's its working

Make a complete backup of the drive or partitions using partimage or a similar tool.

Also set up the scripts to make a backup of the mythconverg database daily. I use a script that backs it up every 4 hours (mc.sql) and then makes a daily backup of the 4 backups. It's set up to rotate out so I always have 7 days worth of the database.. Did this after lightning hit the first box and had to rebuild.  Found out It would have been easier to have copies of the database ready to go. You'll find them all over the internet.


To make it really cool burn some of the recorded programs to dvd. Since you are using a really good card the files should be good to go.  If you cannot nuvexport works but it took a little time to get it installed and working.

Once you have the files in mpg format you can use dvdstyler to create dvd's with menus, or I have a simple method / script that uses dvdauthor and mkisofs to do it without menus.

Each weekend we burn 3 or more dvds of shows we've recorded.  Kids love it -- favorite shows  and no commercials.

Have fun.

---

### Post by williammanda on 2007-03-09
I too want to thank the ubuntu group for the mythtv support. I also went through several distros before getting mythtv to function properly. I would like to see a separate area just for mythtv, if possible.
Thanks

---

### Post by tagra123 on 2007-03-09
It would be super cool to have dvd put together that would work with the wintv throught the pvr models with a simpler setup. Similar to the knoppmyth but with setup wizards for the remotes, cableboxes etc...  I'd participate in that.

I haven't installed in a while but it would have been very nice to have a metapackage that installed mythtv, mysql, lirc, nvidia, atidrivers -- you get the picture  -- and helped you set it up.  Something different from the main or setup interface used only for setting up initially.


We love it but it was a bear to set up.  Mine is still running on breezy. When I upgrade it will be to a completly new system while the old one is still working.



At the time it seemed as though there weas a lot of bouncing back and forth between different programs.  

Some python GUIs or even perl scripts would be very nice to help setup.

---

### Post by superm1 on 2007-03-09
I'm glad to hear things worked out well for you :)
To let you guys know, there is some work going on towards a standalone disk, but no ETA right now.  Also, when feisty rolls around take a look at the two metapackages introduced:

mythtv-backend-master
ubuntu-mythtv-frontend

---

### Post by tagra123 on 2007-03-09
> **superm1 said:**
> I'm glad to hear things worked out well for you :)
To let you guys know, there is some work going on towards a standalone disk, but no ETA right now.  Also, when feisty rolls around take a look at the two metapackages introduced:

mythtv-backend-master
ubuntu-mythtv-frontend

Sounds good.

---

