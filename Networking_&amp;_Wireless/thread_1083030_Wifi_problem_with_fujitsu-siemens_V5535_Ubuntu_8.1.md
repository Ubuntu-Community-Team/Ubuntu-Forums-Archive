---
title: "Wifi problem with fujitsu-siemens V5535 Ubuntu 8.10 64bit"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by Simyager on 2009-02-28
Hi I have a problem with my laptop. I can't use wifi when I use Ubuntu 8.10 64bit but when I use Vista I can(I have dualboot Vista/Ubuntu). I checked some of the forums and none worked for me so far. The reason is probably because my only connection to the internet is through wifi and NO CABLE. I can download when I use Vista using wifi only. I also should mention that I installed Ubuntu 8.10 64bit while using daemon tool and mounted the ubuntu8.10 64bit.iso and was able to install it from within vista without the use of a cd/dvd.

Please can anyone help me, thanks in advance ;)

---

### Post by Simyager on 2009-03-01
Well 16 hours have passed and still nothing yet.
The wirelesscard I have is Atheros AR5007EG
I get on the terminal DISABLED and UNCLAIMED.
I tried to do this:
----------------------------------------------------------------------------------------------------------
>Hello to all my readers, I have recently purchased an Acer Aspire One netbook PC.  The netbook came with Windows XP pre-installed, but I took care of that by installing the new Ubuntu 8.10 Intrepid Ibex.  I chose Intrepid over Hardy as it has better hardware support for the new model Atheros wireless card.

This tutorial will assume that you know how to install Ubuntu.  Since there is no CD drive you will need to use Intrepid Live CD to create a bootable USB drive.  Simply use the .iso you downloaded to create the disc.  When booting up the Aspire One presss F12 with the flash drive installed and install Intrpid as you see fit.

The rest of this tutorial will help you get the wireless and SD card readers functioning.

Things that function OOB are as follows:
- Video including Compiz
- Wired ethernet (I only did this one)
- Touchpad
- Chipset
- Webcan with install of Lucview

Things that need tweaking
- Wireless (I only did this one)
- SD CARD
We will focus on getting the wireless and SD card readers working, so off we go.  This information was gotten from the Ubuntu Community Documentation on the Aspire One.

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

Wireless

The Acer Aspire One has a new model Atheros wireless card.  First thing you need to do is to deactivate the Atheros driver that Intrepid installs as it does not work.  To do this go to System--->Administration--->Hardware Drivers and deactivate the Atheros driver.

Next we will need to load some new kernel modules to get that wireless card working.  To do this open a terminal and type the following:

sudo apt-get install linux-backports-modules-intrepid-generic

Once the drivers load up you will need to reboot the machine.  Once rebooted go back to the Hardware drivers section in SYstem--->Administration and you will see a new entry.  Activate the new Atheros driver and your wireless will work.  Next we need to make sure that kernel module gets loaded each boot so we will need to install

ath5k 

at the end of your /etc/modules file.  Unfortunately the wireless LEDs don't work using the ath5k driver but they do work using the ath_pci madwifi driver.

It has come to my attention that the ath5k driver has issues and problems connecting.  I have devised a script that will automate the install of the madwifi drivers on your Intrepid box.  You will first need to disable all the Atheros drivers in the Hardware Drivers section and remove the ath5k load in the /etc/modules file.  Next do the following in a terminal:

cd ~
wget [http://www.stchman.com/tools/aspire_one/aspire_one_wifi.sh](http://www.stchman.com/tools/aspire_one/aspire_one_wifi.sh)
chmod 755 ~/aspire_one_wifi.sh
sudo ~/aspire_one_wifi.sh

The script will install the madwifi drivers into the kernel and also enable the wifi LEDs.  Remember though when Ubuntu updates ther kernel this module will have to be reinstalled.<
-----------------------------------------------------------------------------------------------------------
After That was finished my laptop rebooted and I chose Ubuntu and I got a blackscreen with lines of codes or libraries something like that I didn't completely understand it though. It said everything was ok but 1 thing failed. And they asked me to check it. So I wrote check and everytime there where lines saying ok and check it. It was my fault I guess and not this guy's fault because it was for the aspire one and not for fujitsu-siemens but I thought I would say it because it could be important.

To make my story short it only happend once and no more. I downloaded those files with vista through wifi. As it is my only connection.

Please help me as fast as you can :)

---

### Post by Simyager on 2009-03-08
Can someone please help me with my internet connection. I am getting desperate and am even thinking of unistalling Ubuntu all together so please help me

---

### Post by Mark V on 2009-11-01
> **Simyager said:**
> Can someone please help me with my internet connection. I am getting desperate and am even thinking of unistalling Ubuntu all together so please help me

What is your current situation?
Have you tried Ubuntu 9.10?

---

