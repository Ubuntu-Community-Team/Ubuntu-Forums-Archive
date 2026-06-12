---
title: "Networkmanager  Toshiba Remix"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by malcollins on 2009-01-05
I have a Toshiba NB100, and the wireless connection seems to be stopping and starting regularly.

The log files show many entries like this

Jan  5 23:22:38 TOSHIBA-User NetworkManager: <info>  Supplicant state changed: 1 
Jan  5 23:27:01 TOSHIBA-User NetworkManager: <info>  Supplicant state changed: 0 
Jan  5 23:27:07 TOSHIBA-User NetworkManager: <info>  Supplicant state changed: 1 
Jan  5 23:27:46 TOSHIBA-User NetworkManager: <WARN>  nm_dbus_get_network_data_cb(): message arguments were invalid (could not deserialize wireless network security information. 
Jan  5 23:28:08 TOSHIBA-User NetworkManager: <info>  Supplicant state changed: 0 
Jan  5 23:28:14 TOSHIBA-User NetworkManager: <info>  Supplicant state changed: 1 
Jan  5 23:29:15 TOSHIBA-User NetworkManager: <info>  Supplicant state changed: 0 
Jan  5 23:29:20 TOSHIBA-User NetworkManager: <info>  Supplicant state changed: 1  

So it seems to starting and stopping

My Wireless adaptor is
Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

The networkmanager is version 0.6

Has anyone experienced this problem

---

### Post by sandman652001 on 2009-01-06
I'm not having any problems with it on my NB100 but I'm not using the standard Toshiba install and my NM is version 0.6.6 apperently the standard toshiba install has a lot of problems this thread might help you [http://ubuntuforums.org/showthread.php?t=993133&highlight=toshiba+nb100&page=4](http://ubuntuforums.org/showthread.php?t=993133&highlight=toshiba+nb100&page=4)

---

### Post by malcollins on 2009-01-10
Thanks Sandman, I have had a look at the thread you mentioned, but as far as I can see it does not do anything to the networkmanager.
I have seen that there are many bugs that have been notified in the networkmanager and that alot of work is being done by the developers.  I&#314;l wait for them to finish and then try an updated networkmanager.
In the mean time I&#314;l just keep deleting the log files now and again.   

malcollins

---

### Post by sandman652001 on 2009-01-11
you could try and follow this part of the guide to see if it soves your problem:

Install Network Manager 0.7 (3g support)

sudo gedit /etc/apt/sources.list

and add the following to the end of the file

deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main

sudo apt-get update

sudo apt-get upgrade

reboot

restart network manager alt+f or from a terminal:

nm-applet

blacklist the airprime driver

sudo nano /etc/modprobe.d/blacklist

Add this to the bottom of the file:

blacklist airprime

Remove the running driver:

sudo modprobe -r airprime

---

