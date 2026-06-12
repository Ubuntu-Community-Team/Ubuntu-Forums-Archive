---
title: "Wireless networks only sometimes showing up"
date: 2010-11-06
forum: Networking &amp; Wireless
---

### Post by LouisaLou on 2010-11-06
Hi, 

I'm a total newcomer to Ubuntu but am enjoying learning the ropes. I apologize in advance for the naivete of my questions...

I arrived in the Central African Republic only to find that my wireless (on an HP Mini 5102) wasn't working -- it didn't detect any wireless networks. So I wiped off Windows and installed Ubuntu 10.10, hoping that would help. Luckily, it did! (Partly.) 

At first, I still didn't get any wireless networks. I messed around with all the various things you have to do to get Broadcom wireless drivers working. Finally, following a forum suggestion, I installed Wicd -- and this did the trick. Not knowing any better, I kept Network Manager alongside Wicd, but Wicd is what works much better. (Is there a reason to un-install Network Manager?)

However, when I try to connect wirelessly to the network at this country's one cafe with wifi (which usually works really well, by CAR standards), the network doesn't appear. At the office, when I open Wicd, it includes a box with the message "<connection name>: obtaining IP address", and bit by bit it connects. But when I open Wicd at the cafe, this doesn't happen -- it just gives me a list of random signals from nearby offices (all secured and low-signal), none of which I can connect to. Any ideas how I could get the cafe network to show up?

I'm at the office now, and so it's working. However, in order to get it working I had to restart three times -- Wicd only seems to work about half or 33% of the time. Sometimes I get the message: "Connection failed: unable to get IP address" and sometimes I get the message "No wireless networks detected." Then I try again and eventually it works. So far. 

Any suggestions/advice would be so much appreciated! I'm headed out to a small provincial town many hours from the capital, and there will be only one wifi connection there, so I'm eager to work the bugs out beforehand. I'm happy to post more technical info, I just need a little guidance!

Thanks so much!!

---

### Post by uncaspi on 2010-11-06
You can connect manually using console. sudo /sbin/dhclient wlan0
Look in sudo /sbin/ifconfig or sudo /sbin/iwconfig to find the right name of the wifi card. Sometimes it`s called wifi0,wlan0 or eth1

---

### Post by uncaspi on 2010-11-06
Lets do it properly. I assume your wireless card is named eth1.
Do the following from console.

sudo /sbin/ifconfig eth1 up

Now we can scan for networks. This is good if you want to see information about the networks in the area. You might already know your access points info but if you don't just scan.

sudo /sbin/iwlist scan

It will give the list of access points, Ad-Hoc cells in range, channels, and a lot more info. My access point was listed and showed it's name "wpatest" on channel 7. So lets configure the wireless interface for that. 


sudo /sbin/iwconfig eth1 essid "wpatest" channel 7


sudo /sbin/dhclient eth1

After this you should have an ip and be on the network. Below is the shell script I use to start my wireless interface. If you know the settings of your access point just change to fit your needs.

#!/bin/sh

sudo /sbin/ifconfig eth1 down
sudo /sbin/ifconfig eth1 up
sudo /sbin/iwconfig eth1 essid "wpatest" channel 7
sudo /sbin/dhclient eth1

Good luck. :)

---

### Post by LouisaLou on 2010-11-07
Hi,

Thanks so much for these tips! I will try them out at the wifi cafe to see if I can get it working and report back. 

Thanks again -- I really appreciate it!

Louisa

---

### Post by uncaspi on 2010-11-07
I forgot to say you must disable network-manager before you apply the commands.

sudo service network-manager stop

---

### Post by LouisaLou on 2010-11-08
Ah -- thanks. I tried the commands you suggested when at the cafe but didn't see this last note until just now. Should I also disable Wicd manager? 

I ran  
sudo /sbin/iwlist scan 
quite a few times. I got three different responses:
I got one of three different responses:
- A couple of weak wifi signals (not the one I was looking for);
- "Failed to read screen data: Invalid argument"
- "No scan results"

Meanwhile everyone around me was happily connected to the cafe wireless network. 

Any additional tips, besides disabling network manager (and Wicd?)?

Thanks so much!

---

### Post by uncaspi on 2010-11-08
Yes stop wicd too

---

### Post by LouisaLou on 2010-11-08
OK, thanks!

---

### Post by LouisaLou on 2010-11-09
Hi,

So, no luck. I went through all the steps -- multiple times -- and still don't see the wireless network I need. I see some assortment of other secured, weak signals in the area (varies which ones), but not the strong, cafe signal. I would think that it is a problem with the network rather than my computer except that everyone else there is connected to it. The cafe wireless has a password -- could that be throwing things off?

Any ideas what else I might try? Or I am just doomed to a fickle wireless card?

Thanks so much!
Louisa

---

### Post by uncaspi on 2010-11-09
No it has nothing to do with the password. I had to think about it what to do :-)

---

### Post by LouisaLou on 2010-11-09
Thank you! I can send a few screenshots if that would help...but I think basically it's working the way that it should, except that for some reason that one network doesn't show up.

---

### Post by BigMkubwa on 2010-11-09
hi, sorry but i am a newbie to.

Am having a similar problem,
im running on ubuntu 10.04 and managed to install my d-link dwa-120 wirless g180 usb adopter.
 The problem is i can actually see my lan but cannot access it nor can i access the wep/wan/gan. 
my card can be detected but cannot connect 
what to do.....HELP :-(

---

### Post by uncaspi on 2010-11-09
Try to disable power saving on the card. I'm not familiar with HP Mini but I think you could try sudo /sbin/iwpriv eth1 set_power 6

You find the logical name eth1,wlan0 or wifi0 using

sudo /sbin/ifconfig

and eventually replace eth1 in the iwpriv command

---

### Post by LouisaLou on 2010-11-09
Help!

Not only did it not work, but now that I am back at my office (where it usually works) wireless is not working here either! When I try to scan for networks using the command line I get the message ¨Failed to read scan data: Invalid argument¨. Wicd and Network Manager are both running but can´t find any wireless networks. Any ideas?

---

### Post by LouisaLou on 2010-11-09
Hi,

I installed WiFi Radar, and that seems to contain all the commands that you laid out, uncaspi. However, I still am failing to get connected wirelessing. I can see some wireless networks, but it gets hung up trying to obtain an IP address. I've been playing around with turning things on and off for a few hours now. Anyone have any other ideas? 

Thanks!!

---

