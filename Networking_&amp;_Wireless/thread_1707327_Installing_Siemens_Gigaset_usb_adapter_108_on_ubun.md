---
title: "Installing Siemens Gigaset usb adapter 108 on ubuntu 10.04"
date: 2011-03-15
forum: Networking &amp; Wireless
---

### Post by danweetikhetooknietmeer on 2011-03-15
Installing Siemens Gigaset usb adapter 108 (wireless usb adapter) on ubuntu 10.04 is simple, just follow the instructions on wifidocsdriverndiswrapper: 


[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
 

or do the following:
 

 Install the ndisgtk package from the Ubuntu repositories.
 

 sudo apt-get install ndisgtk
 

 Run the following command:
 

 sudo ndiswrapper -i ~/drivers/drivername.inf
 

 (assuming the driver is in a directory in your home folder called drivers, and is named drivername.inf; in case of siemens usb adapter 108 use the original windows xp driver (net5523.inf) from the original cd or download it from the internet)  
 

 Run the following command:
 

 ndiswrapper -l
 

 If ndiswrapper correctly associates the driver to the wireless adapter, you are now ready to load the driver into memory, and try to establish a network connection. Run the following commands:
 

 sudo depmod -a
 
sudo modprobe ndiswrapper
 

 Then check for error messages:
 

 tail /var/log/messages
 

 Automatically loading at start-up:
 

 sudo ndiswrapper -m
 

 Edit /etc/modules file to add an entry for ndiswrapper (just put the word 'ndiswrapper' at the end of the file and save).
 

 gksudo gedit /etc/modules
 

 Done!

---

### Post by jakovina on 2011-05-11
I did as described here.
However, I noticed that it works if it is not plugged in USB port during system start-up (if I plug it after system is up and running).

If it is plugged in during system start up it is not working even if I take it out and plug it in again.

Does anyone knows ho to solve the problem or does anyone else have the same problem?

The system is Ubuntu 10.04.2 on old AMD Sempron 2300+ PC

---

### Post by GeneralOJB on 2012-02-23
> **jakovina said:**
> I did as described here.
However, I noticed that it works if it is not plugged in USB port during system start-up (if I plug it after system is up and running).

If it is plugged in during system start up it is not working even if I take it out and plug it in again.

Does anyone knows ho to solve the problem or does anyone else have the same problem?

The system is Ubuntu 10.04.2 on old AMD Sempron 2300+ PC

I'm having the exact same problem! If it's plugged in before startup when I use sudo modprobe ndiswrapper I get errors in the log. But if I plug it in after startup and then use that command it works. 

How do I get it to auto work on startup? I'm using xubuntu and have siemens gigaset usb 108 adapter.. I have used ndiswrapper to install the drivers for it.

---

