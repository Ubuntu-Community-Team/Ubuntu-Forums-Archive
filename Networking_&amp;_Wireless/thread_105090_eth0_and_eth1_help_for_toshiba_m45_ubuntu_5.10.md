---
title: "eth0 and eth1 help for toshiba m45 ubuntu 5.10"
date: 2005-12-17
forum: Networking &amp; Wireless
---

### Post by jeff913 on 2005-12-17
This is my first post to this forum.
Trying to get wireless support working, and lan connectivity on my inhouse wired network from my Toshiba laptop.

Toshiba laptop m45-S269 with Marvell Yukon 88e8036 fast ethernet controller, IPW2200bg network connection, and 1394 net adaptor. Have dual boot with two 5.10 breezy systems and Windows XP, and a fat32 partition to share between ubuntu and XP.
  Have home LAN with breezy on a desktop with Samba, but the laptop running ubuntu 5.10 does not see the lan... ping says other system not reachable, laptop works fine on lan in WinXP.
Breezy installation of 5.10 on the laptop detects eth0 and eth1, but when install is finished ..system..admn.networking does not see eth1.
Have tried several 1pw2200 'fixes' but have never been able to get a clean install.  Tried ndiswrapper, with driver that comes with XP for the laptop, everything clean, but no eth1 on ..system..admin.. networking..
I suspect some interaction betwen the eth0 and eth1 controller.
I am very new to linux, but would love to use it as my primary OS.
Any help would be greatly appreciated.

---

### Post by mlomker on 2005-12-18
[QUOTE=jeff913]Tried ndiswrapper, with driver that comes with XP for the laptop, everything clean, but no eth1 on ..system..admin.. networking..
[/QUOTE]

You wouldn't.  Ndiswrapper makes the interface wlan0 whereas ipw2200 uses eth1.

I think that a better test would be to look at the output of **iwconfig** at a prompt to see if it lists your access point.  I don't trust the graphical tools.  All of the network config is in /etc/network/interfaces.

---

### Post by jeff913 on 2005-12-18
output of iwconfig is

lo      no wireless extensions
eth0  no wireless extensions
 and there was one other??  but NO eth1

I did not know ndiswrapper was wrong to try..

I have tried ipw2200 fix but cannot get clean install.

Regards.....     Jeff

---

### Post by mlomker on 2005-12-19
[QUOTE=jeff913]output of iwconfig is

lo      no wireless extensions
eth0  no wireless extensions
 and there was one other??  but NO eth1

I did not know ndiswrapper was wrong to try..
[/QUOTE]

I didn't say that it was wrong, just that it uses a different interface name.

It would seem that neither driver was loaded properly when you ran that command.  ipw2200 comes with the kernel so installing it shouldn't be necessary.

---

### Post by jeff913 on 2005-12-19
I sent an email to stevewa (laptop tester) and he suggested I add
irqpoll pci=noacpi
to my boot string in /boot/grub/menu.lst, I did and now eth1 appears!!
However I still cannot make a connection.
Following is iwconfig output... 

jeff@ubuntum45:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"public"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:40:96:35:AC:5B
          Bit Rate=11 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=42/100  Signal level=-75 dBm  Noise level=-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

the above is my unmodified ubuntu 5.10
*********************************************
*********************************************
I also have another ubuntu partition, and here I tried again to load a new 
ipw2200-1.0.6 and ieee80211-1.0.3 and ipw2200-fw-2.3  
No visable errors through make and make install, but 
when i do a dmesg I get an error as follows....
jeff@ubuntum45:~$ dmesg | grep ipw
[4294692.691000] ipw2200: version magic '2.6.12-9-386 386 gcc-4.0' should be '2.6.12-9-386 386 gcc-3.4'

this partition has no eth1 from iwconfig command

---

### Post by mlomker on 2005-12-20
[QUOTE=jeff913]
[4294692.691000] ipw2200: version magic '2.6.12-9-386 386 gcc-4.0' should be '2.6.12-9-386 386 gcc-3.4'
[/QUOTE]

I assume that means you compiled the ipw driver with gcc4.0, which you can't do.  The kernel is compiled with 3.4 so all kernel modules must be as well.

Is this 'public' access point an open AP with no encryption or security on it?  Once iwconfig looks correct you should be able to **sudo dhclient** to obtain an IP address.

---

### Post by jeff913 on 2005-12-20
[QUOTE=mlomker]I assume that means you compiled the ipw driver with gcc4.0, which you can't do.  The kernel is compiled with 3.4 so all kernel modules must be as well.

Is this 'public' access point an open AP with no encryption or security on it?  Once iwconfig looks correct you should be able to **sudo dhclient** to obtain an IP address.[/QUOTE]

Yes, I did compile with Gcc-4.0 which comes wuth ubuntu 5.10.  

I just wanted to tell you that I am on ubuntu 5.10 right now making this reply via my ipw2200 wirelesscard.  The problem is that the 'public' access point is not strong enough from the location I was at!!

The 'fix' for my Toshiba M45-s269 laptop was the irqpoll pci=noacpi that I added to the boot string (thanks to SteveWa)

Regards.....     Jeff

Just for my newbie ness... can I download Gcc-3.4.0 and use this to compile fixes for my ubuntu 5.10? (in place of my gcc-4.0)

Thank you for your help...

---

### Post by mlomker on 2005-12-21
[QUOTE=jeff913]Just for my newbie ness... can I download Gcc-3.4.0 and use this to compile fixes for my ubuntu 5.10? (in place of my gcc-4.0)
[/QUOTE]

It's not you...it's been argued that it is a Breezy bug that they don't include the 3.4 compiler.  

```

sudo apt-get install gcc-3.4-base

```

---

