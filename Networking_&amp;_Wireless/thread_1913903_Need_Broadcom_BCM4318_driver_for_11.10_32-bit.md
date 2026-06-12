---
title: "Need Broadcom BCM4318 driver for 11.10 32-bit"
date: 2012-01-23
forum: Networking &amp; Wireless
---

### Post by etherealfocus on 2012-01-23
Found a post at [http://ubuntuforums.org/showthread.php?t=1747147](http://ubuntuforums.org/showthread.php?t=1747147) but not sure how relevant it still is and had some trouble following the thread (warning: newbie alert).

I'm running a Gateway MX6025 laptop with Broadcom BCM4318 wifi card. No driver is discovered by Additional Drivers.

lspci:
02:04.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

WinXP drivers are here if it helps: [http://support.gateway.com/us/en/product/default.aspx?tab=1&modelId=3132](http://support.gateway.com/us/en/product/default.aspx?tab=1&modelId=3132)

I know it's occasionally possible to use Windows drivers in Linux, but I'd imagine native drivers would generally be preferable...?

Thanks for the help! I know newb questions like this can get annoying. :)

---

### Post by mario.niessner on 2012-01-23
Open a terminal and try this:

sudo apt-get install firmware-b43-installer


It works in 11.04, hope the package is available for 11.10.

---

### Post by snowpine on 2012-01-23
Welcome to the forums!

There is so much information out there about Linux, and there is no intelligence test to post on the internet... so sometimes it can be tricky deciding which advice/tutorial/how-to to trust!

My advice is stick with official instructions from ubuntu.com whenever possible. Here is the official page on Broadcom: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

This documentation confirms that Mario is correct and you want the b43 driver (not STA!) for your BCM4318. :)

---

### Post by etherealfocus on 2012-01-24
Thanks guys! Tried your solutions, but the terminal just returns an error. Here's the copy-paste:

geek@geek-MX6025:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-installer
geek@geek-MX6025:~$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package b43-fwcutter
geek@geek-MX6025:~$ 

Tried fwcutter as well, as per instructions on the Broadcom page. Any ideas? I really appreciate the help. :)

---

### Post by salcykhan on 2012-03-12
> **etherealfocus said:**
> Thanks guys! Tried your solutions, but the terminal just returns an error. Here's the copy-paste:

geek@geek-MX6025:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-installer
geek@geek-MX6025:~$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package b43-fwcutter
geek@geek-MX6025:~$ 

Tried fwcutter as well, as per instructions on the Broadcom page. Any ideas? I really appreciate the help. :)


i had the same problem with this driver
well i did solved by diffrent driver which off In Hardy, lspci shows: "Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)"


hope it work for for you



1 --    echo -e 'blacklist bcm43xxnblacklist wl' | sudo tee -a /etc/modprobe.d/blacklist

2 --    sudo apt-get install ndiswrapper-utils-1.9

3 --    mkdir ~/bcm43xx; cd ~/bcm43xx

4 --    sudo apt-get install cabextract

5 --    wget [ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe)

6 --    cabextract sp33008.exe

7 --    sudo ndiswrapper -i bcmwl5.inf

8 --    ndiswrapper -l

9 --    sudo depmod -a

10--    sudo modprobe ndiswrapper

11--    sudo cp /etc/network/interfaces /etc/network/interfaces.orig

12--    echo -e 'auto loniface lo inet loopbackn' | sudo tee /etc/network/interfaces

13--    sudo ndiswrapper -m

14--    echo 'ndiswrapper' | sudo tee -a /etc/modules

15--    echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

follow these 15 steop it worked for my bcm4318

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by bctechnzl on 2012-05-19
For the download of the cabfile, I have a Presario V5000 so according to the hp website, my cabfile was different. I downloaded via wget [http://ftp.hp.com/pub/softpaq/sp39501-40000/sp39912.exe](http://ftp.hp.com/pub/softpaq/sp39501-40000/sp39912.exe)

This when applied along with the other instructions, and of course the cabextract was for this other cabfile, worked for me.

---

