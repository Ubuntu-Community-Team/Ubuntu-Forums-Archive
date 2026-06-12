---
title: "Acer Aspire One ZG5 Ubuntu 10.04 Wifi problem"
date: 2010-10-08
forum: Networking &amp; Wireless
---

### Post by JW1096 on 2010-10-08
Hi there,

I am having difficulty accessing wireless internet with my netbook. Connections are recognised but it fails to connect and the circle just goes round and round. I am connected wirelessly via my laptop and have no ability to connect the netbook via a wired connection. 
I have trawled posts pertaining to my problem on various forums but much of the advice is aimed at users with; a)more experience than me or b)different problem symptoms.

System> Administration> Hardware drivers shows no proprietary drivers.



Acer Aspire One ZG5
2 ) Wireless Brand, Model and Wireless Chipset:
Code:Atheros AR5BXB63


8 ) Ubuntu Version: 10.04

I'm afraid this is all the information I can offer.

Please, please help.

Thanks in advance

Jo.

---

### Post by bayouwillie on 2010-11-05
I'm sure there is a better way to get the wireless working, but I have been doing this since I installed 8.10 on my Acer ZG5, and it works flawlessly in 10.04:

Note: you must be plugged into the ethernet for this work.

Kernal updates of your system will kill your driver. Well no need to worry about that.Just recompile your driver.
For that you open a terminal and type the command
Code:
In Terminal:
Open the 'terminal' by navigating through Applications-->Accessories--> Terminal

Now type the following commands in terminal

1.
Code:

sudo nano /etc/apt/sources.list

From there make sure you uncomment anything that starts with "deb" in there. So changer it from "#deb" to "deb" Something along thoes lines. To exit and save hit "CTRL+X" the answer "YES" to do you want to save, then finally hit "ENTER"

2.
Code:

sudo apt-get update && sudo apt-get upgrade

3.
Code:

sudo apt-get install build-essential libssl-dev

4.
Code:

sudo apt-get install linux-headers-`uname -r`

5.
Code:

sudo apt-get install subversion

6.
Code:

sudo -i

7.
Code:

sudo svn checkout [http://svn.madwifi-project.org/madwifi/trunk/](http://svn.madwifi-project.org/madwifi/trunk/) madwifi-ng

8.
Code:

cd madwifi-ng

9.
Code:


echo "" >> /etc/modprobe.d/blacklist

10.
Code:

echo "#Remove To Install MadWIFI Drivers" >> /etc/modprobe.d/blacklist

11.
Code:

echo "blacklist ath9k" >> /etc/modprobe.d/blacklist

12.
echo "blacklist ath5k" >> /etc/modprobe.d/blacklistCode:



13.
Code:

make && make install

14.
Code:

echo ath_pci >> /etc/modules

Restart your machine

---------------------

---

### Post by pabc on 2010-11-11
i had a similiar issue with a ZG5 and AR5BXB63 chipset. the instructions above will install madwifi (if you replace every instance of blacklist with blacklist.conf and activate them in the hardware drivers after reboot) BUT the madwifi drivers I checked out do not work with this PC/Card.

Out of the box 10.04 worked to a reasonable level so i suspect it's a preferences/options issue - wrong encryption/tkip etc.

The default drivers work but ALWAYS without fail drop the connection if i try to move a file > 10mb around my home network. I solved this by getting the offical XP driver and using those in ndiswrapper and now my connection is rock stable.

---

### Post by tylerdred on 2010-11-28
I am new to linux, I have the same computer, and I am experiencing the same problem. I followed all the steps above, but when I tried step 13, it says:*** No targets specified and no makefile found.  Stop.

When I try installing the driver with ndiswrapper, it says "incorrect driver in red"  in the graphical user interface.

What should I do?  Thanks in advance.

---

