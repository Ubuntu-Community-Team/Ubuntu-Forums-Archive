---
title: "How to install nvidia GEFORCE GTX 660 TI"
date: 2013-04-17
forum: Multimedia Software
---

### Post by igwt007 on 2013-04-17
[SIZE=3]Could someone please help me install the driver called "NVDIA-Linux-x86-64-310.44.run if you could type the actual commands so I can copy and paste them. I it keeps telling me to install as root user and to get out of x-windows. I'm using the terminal window. Thank you.[/SIZE]

---

### Post by CatKiller on 2013-04-18
Don't.

Install using the tools provided; the package manager and the Additional Drivers tool.

---

### Post by oldfred on 2013-04-18
Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

# You may need headers - meta package for current version:
apt-get update 
sudo apt-get install linux-headers-generic

# only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available  versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
 # [ using the correct names] for each driver, before running: 
sudo apt-get purge nvidia*

# Install version you prefer
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett*

 To bring it fully up to date, instead of: 'nvidia-installer --update', use 'nvidia-installer -f --dkms'.
The '-f' option implies the inclusion of: '--update', but will force a re-installation even if the currently installed version is the same as the 'latest' which it will download and install.
The '--dkms' option, with driver versions 3.04.xx and later, will check that 'dkms' is installed and offer the option to register the driver with dkms, so the kernal module gets updated automatically when a new kernal is installed. and does not need to be manually re-installed.

---

