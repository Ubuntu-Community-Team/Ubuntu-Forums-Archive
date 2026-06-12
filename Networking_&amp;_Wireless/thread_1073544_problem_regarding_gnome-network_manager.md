---
title: "problem regarding gnome-network manager"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by MastroLindo on 2009-02-18
Hi all.

I have been trying for 2 days to make a netgear wg111v2 work with ubuntu 8.10 with the ndiswrapped drivers from windows xp. (after having failed using an atheros card with madwifi drivers, but that is another story).

I spent almost 2 days just do and redo step by step guides and trying almost everything. Nothing, I could make the usb card work but not connect to the AP.

Just to try I tried, once the drivers where up and running, to connect through the gnome network manager...and it worked.
I couldnt figure it out before since I was accessing the machine through ssh until the last try.
But since my problem is to be able to setup the connection through command line (since I will have to use some specific software for sending radius EAP supplicant messages to the AP), I need to know (and I want to know :)) why it still doesn't work from the command line while gnome manager works without problems.

When my drivers are loaded I usually do

sudo iwconfig wlan0 essid ESSIDNAME
and then if I have dhcp i use
sudo dhclient wlan0

but since I wanted to have static IP assigned I tried
sudo ifconfig wlan0 IPADDRESS netmask NETMASK
sudo ifconfig wlan0 up
.

with iwconfig I can see that the wireless lan is assigned to the right AP mac address (and channel and all the rest) but I can't ping or do anything. If i connect through gnome manager I instead can ping and do everything. 

There must be then a configuration problem that I am missing in the command line configuration.... anybody knows what it can be?

---

### Post by MastroLindo on 2009-02-19
is it possible that networkmanager and iwconfig utilize different drivers? 

I really can't understand why command line connection doesn't work (attaches to the AP but can't ping, dhcp or anything else) and nm works...

---

### Post by MastroLindo on 2009-02-19
i have just found out that the drivers used are indeed different.

Networkmanager is using rt18187(that I thought I had blacklisted in /etc/modprobe.d/blacklist), and removing ndiswrapper didn't create problems for it (it still works) while using iwconfig without ndiswrapper I couldn't access the AP before. So now I have just to find out how to configure wlan0 from command line to use rt18187 drivers as well (I hope this will be less problematic.. )

---

### Post by Corniger on 2009-02-19
[Same problem 1]("http://ubuntuforums.org/showthread.php?t=1072873&highlight=wg111v2")
[Same problem 2]("http://ubuntuforums.org/showthread.php?t=1060214&highlight=wg111v2")

I just reinstalled 810 for the 6th time. No connection, no help. No "Networkin" menu item. No "network configuration utility" for ndriswrapper tutorial.

My personal recommendatio: forget that nonsense.
I'm trying this for the last time now, then I'll try 804 and tell you whether it's worth spending time on this or not....

---

### Post by MastroLindo on 2009-02-19
[http://ubuntuforums.org/showthread.php?t=1074410](http://ubuntuforums.org/showthread.php?t=1074410)

---

