---
title: "MCC crashes on backup file location selection"
date: 2015-09-30
forum: Mythbuntu
---

### Post by vidtek on 2015-09-30
I´ve been using MCC for myth database backups for years and it&#347; saved me many times from the wrath of 
¨SHE¨......  Since a recent update, whenever I attempt a backup through the MCC interface I go through all the steps and when it gets to selecting the folder location for the backup, as soon as I select ¨other¨ MCC just disappears.
I´ve searched through the documentation such as there is (there is an extreme paucity of information on this feature), and hasn´t thrown any light on it.  It seems either nobody else has this problem or it just hasn´t been reported anywhere. 
System:Mythbuntu  64-bit Kernel 3.19-0-28-generic  Kubuntu 14.04
mythtv:
  Installed: 2:0.27.5+fixes.20150921.fbd5ef3-0ubuntu0mythbuntu3
  Candidate: 2:0.27.5+fixes.20150930.2ad3158-0ubuntu0mythbuntu3
  Version table:
     2:0.27.5+fixes.20150930.2ad3158-0ubuntu0mythbuntu3 0
        500 [http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/](http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/) trusty/main amd64 Packages
 *** 2:0.27.5+fixes.20150921.fbd5ef3-0ubuntu0mythbuntu3 0
        100 /var/lib/dpkg/status
     2:0.27.0+fixes.20140324.8ee257c-0ubuntu3 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates/multiverse amd64 Packages
     2:0.27.0+fixes.20140324.8ee257c-0ubuntu2 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/multiverse amd64 Package

Tony.

---

### Post by vidtek on 2015-10-07
It appears that this is a reported bug here  [https://bugs.launchpad.net/ubuntu/+source/gtk2-engines-oxygen/+bug/1242801](https://bugs.launchpad.net/ubuntu/+source/gtk2-engines-oxygen/+bug/1242801)

The fix for me was to modify the file:  /usr/share/themes/oxygen-gtk/gtk-3.0/gtk.css

GtkComboBox-appears-as-list: 1;

to

GtkComboBox-appears-as-list: 0;  

This thread pointed the way for me.   [https://github.com/FreeRDP/Remmina/issues/518](https://github.com/FreeRDP/Remmina/issues/518)       Pretty obscure though, it seems to fix it.

I&#314;l mark this as solved.

Tony

---

