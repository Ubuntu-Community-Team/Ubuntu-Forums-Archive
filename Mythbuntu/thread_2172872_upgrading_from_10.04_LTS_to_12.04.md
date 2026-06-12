---
title: "upgrading from 10.04 LTS to 12.04"
date: 2013-09-06
forum: Mythbuntu
---

### Post by kbrunsting on 2013-09-06
I'd really like to update to the latest LTS version and I was wondering if there are things I need look out for.  10.04 has worked well, although I had problems when I swapped in a new motherboard and the realtek audio chipset didn't work and I had to compile the alsa driver (solution found on this forum) which worked, but I'm hoping 12.04 will detect the audio properly.   Other than that, I think that the newest myth version changes lirc?  Generally will it update lirc ok?  I have a older mceusb microsoft remote.  Any other things I should do before attempting this?

---

### Post by bcschmerker on 2013-09-06
An Ubuntu® dist-upgrade from 10.04.7-LTS Lucid Lynx™ to 12.04.3-LTS Precise Pangolin™ has several issues that call for a backup of user documents, a clean ("Custom") installation of the upgrade OS, and restoration of user documents to the upgraded system.  Numerous Packages are incompatible between 10.04.7-LTS and 12.04.3-LTS due to changes in dependencies, as I found out the hard way taking my "Hot Rod gPC" from 10.04.4-LTS to 12.04-LTS back in April 2012.  Additionally, many Programs in 12.04-LTS have had changes in "dot-programname" data formats compared to their 10.04-LTS counterparts.

---

### Post by oldfred on 2013-09-07
Definitely use live installer to test your system.

I had upgraded from 6.06 to 9.04 every 6 months and had issues. When I did a clean install to 9.10 to convert to 64 bit it worked so well that I only do clean installs.

My backup procedure is to recovery all my data and list of installed applications, so I can reinstall and restore my system.

 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
      
 Some files to exclude from /home backup - post by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

 More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

Your package list from dpkg may include a lot of apps that have changed. It may include some obsolete ones, but they will not be installed. For instance, you may have OpenOffice and new install will install LibreOffice, but you do not need nor really want to install OpenOffice as it may create conflicts. List of apps is just a text file so you can delete at will.

      
 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

---

### Post by kbrunsting on 2013-09-08
So a couple things.... I have basic knowledge of linux and I have a pretty much out of the box mythbuntu installation.  So when you recommend a clean install (other than backing up home and some directories in etc), does that mean a re-install?  If I download and run the live installer for mythbuntu 12.04, at some point am I reformatting partitions and re-setting up mythtv?

---

### Post by oldfred on 2013-09-08
I do not know about Myth. It has a lot of settings but has been upgraded a lot.

---

