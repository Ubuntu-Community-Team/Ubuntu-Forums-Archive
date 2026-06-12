---
title: "Wireless Driver?"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by yungpiz on 2009-11-08
Hi,
 
I recently installed Ubuntu 9.10 Netbook Remix on my old HP Pavillion DV1000 laptop.  I clicked the network connections icon in the top toolbar and the wireless networks will not even display in the list.
 
There is a physical button on the laptop's keyboard used to activate the wireless adaptor.  When Windows was installed, if you pressed that button, it would illuminate and it no longer illuminates when pressed.  I am assuming this is a driver issue?
 
When I go to HP.com and search for the wireless driver, I get this:
Broadcom WLAN driver Version 3.100.65.1
 
and the file name of the download is [[COLOR=#003366]SP30379.exe[/COLOR]]("ftp://ftp.hp.com/pub/softpaq/sp30001-30500/SP30379.exe"), which I am pretty sure won't work with Linux....
 
If anyone has run into a similar problem and knows how to help, I would GREATLY appreciate it.  I'm new to Ubuntu/Linux :-)
 
Thanks,
Jay P

---

### Post by puppywhacker on 2009-11-08
I'm unfamiliar with your specific laptop and HP only specifies "Broadcom" and they made a LOT of network interfaces. A LOT! It would help if you could open a terminal and type "lspci". In the output you will find the Ethernet controller: Broadcom and the model number.

If you can find the model number we can guide you trough the process of loading the correct module. It will look like this

```
sudo modprobe b43
```

---

### Post by yungpiz on 2009-11-08
Okay awesome... it printed a bunch of lines.  I think this is teh line you need:
 
06:06:0 Network Controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by puppywhacker on 2009-11-08
That is the line. BCM4318. There are some complications, since the drivers are not officially released the firmware has to be cut from the original drivers with b43-fwcutter. It's just one of those really annoying things when vendors do not support linux. The other option is to use ndiswrappers to use windows drivers under linux. I find ndiswrappers ugly.

I googled quickly and found that you can install the following two packages
sudo apt-get install linux-backports-modules-karmic b43-fwcutter

The linux drivers come from this page
[http://linuxwireless.org/en/users/Drivers/b43]("http://linuxwireless.org/en/users/Drivers/b43")

---

### Post by yungpiz on 2009-11-08
Hmm... I typed:
[COLOR=red]sudo apt-get install linux-backports-modules-karmic b43-fwcutter[/COLOR]
in the terminal and it printed that "package 'linux-backports-modules-karmic' cannot be found".
 
I'm not too familiar with terminal language or anything Linux-related really, but I don't have an internet connection at all on that computer.
 
I am basically just using that computer temporarily and need to be able to connect to the internet because I won't have access to this computer after today.  That being said, I do not care too much about ugliness, so would you recommend the other program maybe?  I am using a windows PC right now so I think my solution will involve downloading some stuff and transferring it to the other laptop via a USB drive.
 
I am kind of lost on how to install the b43-fwcutter and I couldn't find anything more on that link.  Any other help/clarification would be greatly appreciated.

---

