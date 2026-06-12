---
title: "D Link G132 WIRLESS ADAPTER  and UBUNTU"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by Howinlinux on 2008-12-12
I just want to post an installation guide and general information offering for those of you that are using the D-link G132 USB Wireless Adapter and Ubuntu.  It is pretty easy, but finding answers for it have been kind of difficult. Here goes....

INSTALLATION

You will need to manually install the driver using a program called NDISWRAPPER and you may want a 'GUI' based program called NDISGTK.

1.  Copy your driver files to your 'filessytem' where ever you want.
***These files are the ones needed***
athfmwdl.inf
NetA5AGU.inf

BEFORE MOVING FORWARD:Make sure the device is present-
open a terminal and type:
lsusb
u should see all the usb devices listed and one should be from D-Link.
**KEEP YOUR TERMINAL OPEN**

2. Install NDISWRAPPER
sudo apt-get install ndiswrapper

3. Install NDISGTK
sudo apt-get install ndisgtk   or....
use the software manager, it is in the reps.
**you do not have to have NDISGTK to make your device work

**********HERE WE GO************************
4. Installing the Drivers using NDISWRAPPER
ok, now you are going to load the drivers (need both drivers)

open a terminal and navigate to the directory you put the drivers in and type:
sudo ndiswrapper -i athfmwdl.inf <enter>
sudo ndiswrapper -i NetA5AGU.inf <enter>

NOTE: If you are not in the correct directory you must specify the path to where they are.  If you are specifying a path, remember that Linux is 'case sensitive', the path must be right exactly!

5. Check to see that the driver is installed
type the following:
sudo ndiswrapper -l
and it should list both the drivers.

You will need to reboot using a "HARD" shut-down after these steps.  Your device will probably not be working yet until you do.  

GENERAL INFORMATION

***SOME NOTES ABOUT REBOOTING AND DUAL-BOOTING USING WINDOWS***
2.  Any time you use the "restart", this driver does not load on restart.  Use the "Hard" shut-down method and repower after the shut-down instead.

3.  After installing drivers, rebooting into Windows the first time may result in a blue screen of death on the A5AGU driver.  Simple fix, unplug the card, boot fully into Windows, then insert the card.  You will only have to do this one time in most cases, but if you experience it later on, just boot without the card in until you get to your desktop.

I hope that this helps you guys out!  This card is kind of a nightmare to deal with but once you get it configured and fall into the routine you will be connected and maintain the same success you had using it in Windows. 

*****Another Note******
The D-Link G132 has to be uninstalled and reinstalled when you upgrade from Gutsy Gibbon to Heron 8.0.4. There is a regression in which the driver ceases to function after your upgrade is complete.  When I get an answer I will post it.

Jason Brogdon
Dallas, Texas

---

