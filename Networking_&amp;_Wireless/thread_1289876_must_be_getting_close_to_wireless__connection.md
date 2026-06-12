---
title: "must be getting close to wireless  connection"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by rkulas on 2009-10-12
I’m a newbie who finally decided to take the leap.  I don’t know where this post belongs, so kindly point me in the right direction if I am in the wrong pew.  And I will probably be embarrassed when I get this figured out.
   
  I just installed Ubuntu 9.04 and have been trying to get a usb wirless adaptor to work.  It is a D-Link DWA-130.  I have been studying whatever I can find on using the ndiswrapper.
   
  I downloaded it to a usb stick from my Windows machine and created a directory in the “home/ray” folder.  I then created a folder named “wd” (Wirless Devices) and then “dwa130” (the D-Link adaptor) and finally a directory called “files”.  So the complete path is “home/ray/wd/dwa130/files”
   
  So in this directory I now have 5 files:
  ndiswrapper-common_*.deb 
  ndiswrapper-utils*.deb 
  ndisgtk_*.deb 
   
  and the files that I moved from the wireless adaptor installation CD:
   
  netmv245.inf
  mrvw245.sys
   
  I gather that the next step is to install the .deb files.
   
  When I start the terminal and use the commands below I get an error message, so I am assuming that I need to navigate to the directory where these files live and then enter the command:
   
  sudo dpkg -i ndiswrapper-common_*.deb

sudo dpkg -i ndiswrapper-utils*.deb

sudo dpkg -i --force-depends ndisgtk_*.deb   
  I have taken a look at the Using the Terminal page and can invoke commands like:
   
  ray@ray –desktop:-$ ls
   
  where I get the expected results and the directory “wd” appears in the list.  However I can’t seem to navigate to the directory where these file are located by using the command:
   
  ray@ray –desktop:-$ cd /wd
   
  I get the following:
   
  bash: cd/wd: No such file or subdirectory
   
  So I am wondering why I am getting this result. A stupid question no doubt!
   
  I am also wondering if I could move these 5 files to the “ray” desktop” folder and execute them from there.  If so can I delete them after they do whatewver it is they are supposed to accomplish like an install exe file download in Windows?  i.e. will the command put them where they belong?
   
  The next challenge will be to disable the existing wireless adaptor that comes with Ubuntu, but I will cross that bridge when I come to it.
   
  Any help would be appreciated.  I think that my life will get a great deal simpler when I finally get Internet connectivity on the Ubunti machine.
   
  Any help and encouragement would be appreciated.
   
  Ray

---

### Post by bkratz on 2009-10-13
> **rkulas said:**
> I’m a newbie who finally decided to take the leap.  I don’t know where this post belongs, so kindly point me in the right direction if I am in the wrong pew.  And I will probably be embarrassed when I get this figured out.
   
  I just installed Ubuntu 9.04 and have been trying to get a usb wirless adaptor to work.  It is a D-Link DWA-130.  I have been studying whatever I can find on using the ndiswrapper.
   
  I downloaded it to a usb stick from my Windows machine and created a directory in the “home/ray” folder.  I then created a folder named “wd” (Wirless Devices) and then “dwa130” (the D-Link adaptor) and finally a directory called “files”.  So the complete path is “home/ray/wd/dwa130/files”
   
  So in this directory I now have 5 files:
  ndiswrapper-common_*.deb 
  ndiswrapper-utils*.deb 
  ndisgtk_*.deb 
   
  and the files that I moved from the wireless adaptor installation CD:
   
  netmv245.inf
  mrvw245.sys
   
  I gather that the next step is to install the .deb files.
   
  When I start the terminal and use the commands below I get an error message, so I am assuming that I need to navigate to the directory where these files live and then enter the command:
   
  sudo dpkg -i ndiswrapper-common_*.deb

sudo dpkg -i ndiswrapper-utils*.deb

sudo dpkg -i --force-depends ndisgtk_*.deb   
  I have taken a look at the Using the Terminal page and can invoke commands like:
   
  ray@ray –desktop:-$ ls
   
  where I get the expected results and the directory “wd” appears in the list.  However I can’t seem to navigate to the directory where these file are located by using the command:
   
  ray@ray –desktop:-$ cd /wd
   
  I get the following:
   
  bash: cd/wd: No such file or subdirectory
   
  So I am wondering why I am getting this result. A stupid question no doubt!
   
  I am also wondering if I could move these 5 files to the “ray” desktop” folder and execute them from there.  If so can I delete them after they do whatewver it is they are supposed to accomplish like an install exe file download in Windows?  i.e. will the command put them where they belong?
   
  The next challenge will be to disable the existing wireless adaptor that comes with Ubuntu, but I will cross that bridge when I come to it.
   
  Any help would be appreciated.  I think that my life will get a great deal simpler when I finally get Internet connectivity on the Ubunti machine.
   
  Any help and encouragement would be appreciated.
   
  Ray




Do you know which  of the four versions of the unit you have?  There is a -a1 ,-b1, -c1 and I think even a -d1.  I have the -a1 which I am using with Ndiswrapper for this communication.  If you wish to PM me I will give you detailed description of exacly how to proceed. If you are using the same version it is not as hard as it seems.

Brian

---

