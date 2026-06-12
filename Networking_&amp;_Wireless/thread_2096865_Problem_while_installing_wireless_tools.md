---
title: "Problem while installing wireless_tools"
date: 2012-12-21
forum: Networking &amp; Wireless
---

### Post by prasunjit on 2012-12-21
Hello All,

I have been trying for the past few days to connect to the internet , but nothing is working out. Here are the specifiactions.
I am having Ubuntu 10.04.3. LTS Lucid Lynx- Release i386 ( Dual boot with Windows XP)
I am trying to connect to a wireless router (alreaady configured) connected to a ethernet modem, from the command line ( i dont have GUI)
 Wireless card: Intel corp PRO/Wireless Golan

Where do i start?

after googling i understood i have to install wireless_tools package to get my wireless networking get started.

The command - sudo apt-get install wireless-tools failed with the below error.
cdrom://Ubuntu 10.04.3. LTS Lucid Lynx- Release i386/pool/main/wireless-tools file not found

Can someone please help me to undersatnd where am i making mistake or please tell me step by step how to get started ?

I am following the below link to connect to my wireless network
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

### Post by cwsnyder on 2012-12-21
To begin with, the error you are getting tells you that you do not have the wireless-tools package installed on the cdrom from which you installed Ubuntu.  You are going to have to download it in .deb file form(probably through Windows), save it on something which you can read from Ubuntu (if you don't have Ubuntu set up to read your Windows partition, then use **dpkg -i wireless-tools.deb** to install the package.

If you are going to use the guide to set up your wireless configuration, you will need a working Internet connection (_not wireless_) before you start.  Otherwise, you will be going back and forth between your Windows and your Ubuntu install.

It is normally recommended that you get your computer as completely set as possible with a Live disk prior to installing on a new computer, so that all of the packages you need are available.  For example, if you are installing with the alternate install disk, you have thoroughly tested the system and have a working Internet connection to install updates prior to attempting the installation.

---

