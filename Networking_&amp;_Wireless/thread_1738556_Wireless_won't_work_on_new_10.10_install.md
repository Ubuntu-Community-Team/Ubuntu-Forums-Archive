---
title: "Wireless won't work on new 10.10 install"
date: 2011-04-24
forum: Networking &amp; Wireless
---

### Post by bill_meilahn on 2011-04-24
I installed Ubuntu 10.10 (Desktop) two weeks ago on a 933Mhz Dell Lattitude X200 with 
120 gig HD, 512mb memory and built-in wireless, and can't connect to a wireless router. 

I do not have the docking station that came with the machine (a Firewire interface).

I need to connect to a 128-bit WEP encrypted Belkin router. The router 
is used by many, many others, so cannot be brought down for experimentation.
I have tried setting up a wireless connection with NetworkManager and 
iwconfig, but neither seem to work.

Until two weeks ago, this machine was loaded with XP3, and accessed the same
router perfectly.

I can ping 127.0.0.1, but nothing else outside my machine. "Network is 
unreachable." Ergo, IP stack is apparently OK.

Network Manager keeps popping two minutes, prompting me to re-
authenticate. (Should I delete NM?  How may this be done?)

iwconfig reports eth1 as listening/broadcasting on 2.457.  However, the router is 
set to channel 6, 2.437G.  iwlist scan detects the router correctly on 
channel 6/2.437G.  

When I try to reset the frequency or channel with iwconfig, the 
transaction fails with and error message, "Error for wireless request 
"Set Frequency" (8B04): SET failed on device eth1; Device or resource 
busy."  

Similarly, I can't change the channel/frequency by changing inside 
/etc/network/interfaces:  regardless of what I do, restart, 
reboot, deleting the wireless connection in Network Manager, it just 
stays wrong!

ifconfig reports apparently good hardware address, UP BROADCAST MULTICAST, a 
good inet address, bcast address, and mask address.

I tried the following commands with wconfig:

iwconfig eth1 essid myssid
iwconfig eth1 mode managed
iwconfig eth1 key my26charhexkeylookslikthis
iwconfig eth1 freq 2.437G
dhclient eth1

I added the following lines to /etc/network/interfaces:

auto eth1
iface eth1 inet dhcp
   wireless yes
   wireless-mode managed
   wireless-essid myssid
   wireless-key my26charhexkeylookslikthis
   wireless-channel 6    

When I restart the network, I get the following dmesg's:

- ADDRCONF (NETDEV_UP) eth1; link is not ready (many!)
- Lots of orinoco_cs 0.15 messages, so the driver is apparently ok
- eth1: Lucent/Agere firmware doesn't support manual roaming (many, many!!)

lshw shows a 3Com 3c905c-TX/TX-M Network Ethernet interface as eth0, and eth1 as
the wireless interface with the Orinoco_cs 0.15 version 2.6.35-22 driver apparently installed OK.

I am new to Linux, but have learned a lot these past two weeks... mostly about how difficult it can be to install wireless support.  Can anyone help me figure out what to do next?

---

### Post by uncaspi on 2011-04-24
I read on a thread that there is a problem with 10.10 and WEP. It helped by switching to WPA-2

---

### Post by fabsbsd on 2011-04-25
Hi!

Please post the last 40 lines from dmesg just after ou try to connect, let's see what does your kernel say

Cheers!

---

### Post by frank604 on 2011-04-25
What is your network controller?

Type lspci | grep -i net
and enter data in thread.  Perhaps it is a driver issue of not loading up the correct driver, as is the case for many Ralink chip cards.

---

### Post by Rasa1111 on 2011-04-25
> **uncaspi said:**
> I read on a thread that there is a problem with 10.10 and WEP. It helped by switching to WPA-2

my 10.10 doesn't have a problem with it.
Don't even need to activate any extra drivers. 

 I didnt see OP say anything about additional drivers..

Did you see if there were any additional drivers available?
If so, did you try any of them?

 Everytime Ive not been able to get wireless working out of the box.. Finding and activating the proper driver in "Additional Drivers" in **System**>**Administration**> **Additional Drivers**. 

8 out of 10 times though, wireless just works "out of the box" for me. 

Sorry if youve already tried this..
But if not, it's usually a very simple solution, in my experience anyway. 

Good luck.

---

### Post by bill_meilahn on 2011-04-25
All:  Thanks for your interest and suggestions.  Responses follow:

Can't switch to WPA... not my router.  Have to use WEP key as given.

The network controller is the 3Com 3c905c-TX/TX-M cited above.  The  lspci grep confirms this:  "Ethernet Controller 3Com 3c905C TX/TX-M  [Tornado] (rev 78)".  Present driver is Orinoco_cs 0.15.

The kernel is 2.6.35-22-generic.  I have no way to get the dmesg output  to this (Windows 7) machine since the Ubuntu box is not on the network  yet.  Is there something else, specific, I should look for?

There are apparently no more drivers available.  "Finding and activating the proper driver in "Additional Drivers" in **System**>**Administration**> **Additional Drivers**" comes up with nothing.

What next??

---

### Post by Rasa1111 on 2011-04-25
Darn.
Sorry Bill.

 I am unsure of where to go from here.. my apologies.
But I see you last posted 9 hours ago and wanted to give it a BUMP in case someone else more knowledgeable is hanging around...

Hope you get it worked out man.
Good luck. <3

---

### Post by bill_meilahn on 2011-04-26
Update:

Thinking there may be some sort of conflict or unseen pecking order issue between Network Manager and the entries in /etc/network/interfaces, I removed/purged Network Manager, and have restarted networking from the command line.  No Joy.  Three problem areas persist:

1)  There is still an inconsistency between the frequency of the router, and what iwconfig shows.  When I attempt to re-set the channel/frequency, I still get the "device busy" message.  What do I do to "un-busy" the device?

2)  dmesg still reports, " ADDRCONF (NETDEV_UP) eth1; link is not ready."  (This went from many occurrences to only three after the remove/purge."

3)  dmesg also still reports, "- eth1: Lucent/Agere firmware doesn't support manual roaming."  (This went from many, many occurrences to many, many more!)

Any ideas or suggestions would be appreciated!
-

---

