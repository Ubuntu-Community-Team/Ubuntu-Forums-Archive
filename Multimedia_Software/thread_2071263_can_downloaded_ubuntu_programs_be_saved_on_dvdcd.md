---
title: "can downloaded ubuntu programs be saved on dvd/cd?"
date: 2012-10-15
forum: Multimedia Software
---

### Post by SummerT on 2012-10-15
I downloaded the ubuntu installation program onto a CD as I was having a lot of computer issues and needed to wipe my computer with a clean install.  As such, all of my programs which I downloaded while on ubuntu before were lost and I have to now put back on.  Is there an easy way to create a type of recovery cd that will save all of those downloaded programs onto CD like an installation disk so that if I have to wipe my computer clean again, I can just pop this CD back in?  Or can I create a full installation/recovery CD that contains the ubuntu operating system along with the programs I want to download/keep?

---

### Post by SummerT on 2012-10-15
... Or is there an easy way to put the unbuntu entire distribution (O.S. and downloaded programs) on a USB and/or dual layered disc (for example), so that I can run it wherever and whenever I want from said USB or disc?

---

### Post by Cheesemill on 2012-10-15
> **SummerT said:**
> ... Or is there an easy way to put the unbuntu entire distribution (O.S. and downloaded programs) on a USB and/or dual layered disc (for example), so that I can run it wherever and whenever I want from said USB or disc?
Take a look at [Remastersys]("http://www.geekconnection.org/remastersys/index.html").

---

### Post by tienlbhoc on 2012-10-15
or use aptoncd

---

### Post by jerrrys on 2012-10-15
There are lots of ways

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=backup+installed+packages&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=backup+installed+packages&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by ALinuxWindowsBalance on 2012-10-15
> **SummerT said:**
> I downloaded the ubuntu installation program onto a CD as I was having a lot of computer issues and needed to wipe my computer with a clean install.  As such, all of my programs which I downloaded while on ubuntu before were lost and I have to now put back on.  Is there an easy way to create a type of recovery cd that will save all of those downloaded programs onto CD like an installation disk so that if I have to wipe my computer clean again, I can just pop this CD back in?  Or can I create a full installation/recovery CD that contains the ubuntu operating system along with the programs I want to download/keep?

I know in Fedora you can make a Service Pack with the apps you have.
In Ubuntu, you have to go to **/usr/gnome/share/apps** and copy 'em to a flash disk.

---

### Post by oldfred on 2012-10-15
You are into backup & restore. There are many ways to do it.

discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)
Tar backup script:
[https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html)

I think images get old quickly, and just have a home system. So my backup is just another total reinstall. So I backup /home and a list of installed applications to redownload. If you save apps, they may have been updated or you can get out of sync on dependencies. 

Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

Offline Synaptic Installation/Repository Updates 
[http://ubuntuforums.org/showthread.php?t=1901446](http://ubuntuforums.org/showthread.php?t=1901446)
[http://ubuntuforums.org/showthread.php?t=1900550](http://ubuntuforums.org/showthread.php?t=1900550)

Location of downloaded debs
/var/cache/apt/archives/

Offline Updates:
[http://keryxproject.org/](http://keryxproject.org/)
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
Download once for many machines
How To Install Apt-Cacher-NG in Ubuntu Linux
[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)
Location of downloaded debs
/var/cache/apt/archives/

---

### Post by SummerT on 2012-10-16
Thank you to everyone for the valuable information.  Is there a way to save everything (the O.S. with all the personal stuff and programs) on a USB that can run on any computer (including being able to run on a computer that only has windows)?  Sometimes I have to use a different computer when I travel and there have been times that I had one that only had Windows and wanted to run my ubuntu programs.  It would be sort of like a mini computer on a USB.

---

### Post by Cheesemill on 2012-10-16
> **SummerT said:**
> Thank you to everyone for the valuable information.  Is there a way to save everything (the O.S. with all the personal stuff and programs) on a USB that can run on any computer (including being able to run on a computer that only has windows)?  Sometimes I have to use a different computer when I travel and there have been times that I had one that only had Windows and wanted to run my ubuntu programs.  It would be sort of like a mini computer on a USB.
Yes there is, take a look at post #3.

---

### Post by jerrrys on 2012-10-16
Also here

[http://www.pendrivelinux.com/creating-an-ubuntu-live-usb-from-cd/](http://www.pendrivelinux.com/creating-an-ubuntu-live-usb-from-cd/)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by rajeevisonline on 2012-10-16
> **SummerT said:**
> Thank you to everyone for the valuable information.  Is there a way to save everything (the O.S. with all the personal stuff and programs) on a USB that can run on any computer (including being able to run on a computer that only has windows)?  Sometimes I have to use a different computer when I travel and there have been times that I had one that only had Windows and wanted to run my ubuntu programs.  It would be sort of like a mini computer on a USB.

yes please....remastersys

---

