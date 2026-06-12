---
title: "Wireless card not working; have read threads, tried ndiswrapper etc. Please help!"
date: 2006-05-13
forum: Networking &amp; Wireless
---

### Post by Durito on 2006-05-13
I've been grappling with my wireless card for about a week. It worked out of the box with SuSE 9.0, but no luck on Ubuntu. It's quite possible, being a newcomer, that I'm screwing up something basic. Any help will be deeply appreciated. Here's the play by play:

1. Install Ubuntu on second primary partition. Boot up. Network settings shows device as eth0, but after configuring and activating cannot connect to internet.

2. Run 'sudo lshw -C network'. Output shows that module adm8211 has been loaded and associated with the card. 

3. Attempt to connect, configuring card with iwconfig. No luck. Try scanning with iwlist. Receive "resource temporarily unavailable message", though my Windows machine is connected. 

4. Decide, after reading a couple of other threads, that adm8211 does not work with this card, at least in Ubuntu. Use rmmod to unload it, and then blacklist it to prevent loading on boot. Running 'lshw -C network' verifies that card is now unidentified.

5. Install ndiswrapper and load XP drivers for card. Run 'ndiswrapper -l', and see that driver and hardware are present. Run 'depmod -a', and then 'modprobe ndiswrapper'. Run lshw to verify that driver is associated with card.

6. Attempt to configure again with Network Settings. Now device is listed as wlan0. Configure with ESSID 'Any' and DHCP. Does not connect.

7. Go to command line and run ifconfig. Everything looks right except that there is no IP address. 

8. Run 'iwlist eth0 scan', which now returns "No scan results". Gnash teeth in frustration. 

9. Run iwconfig. Settings look all right, and apparently some packets have been sent and received. The right channel has been automatically found, interestingly enough. 

10. Just out of habit, run dhclient. No dice. DHCPDISCOVER goes out on 255.255.255.255 port 67, but no DHCPOFFER is received. Dammit.

11. Reboot, and try steps 5 through 11 again. Still nothing. ](*,) 

What am I doing wrong? I've been fighting with this thing for well over a week now. I really want to use Ubuntu, and if I can just get my wireless up so I can take care of my other work, I'll just trouble shoot the sound and other problems at my leisure. But I've got to get wireless working. 

I'm running Breezy on a Thinkpad 600E. No connection to the internet except through the wireless card. 

Thanks in advance for the help.

---

### Post by cantormath on 2006-07-31
Alright, 
if it worked with suse, you probably do not need suse.

Reboot the machine with card in and tell me what iwconfig and ifconfig says from terminal.
also, try 
sudo dhclient
give it some time and tell me what that says.
make sure you have all the updates installed if this is a fresh install.

---

### Post by Titus A Duxass on 2006-07-31
Have you disabled your on-board eth0, sometimes doing that and rebooting will get your card to come up as wlan0.

You want to take a look at your /etc/network/interfaces file and see if it has wlan0 entries.

---

### Post by Grog140 on 2006-08-04
I have a siliar problem and when I do the dhclient I get:
```

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:0b:7d:06:17:36
Sending on   LPF/wlan0/00:0b:7d:06:17:36
Listening on LPF/eth0/00:11:43:71:33:b9
Sending on   LPF/eth0/00:11:43:71:33:b9
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPACK from 192.168.1.1
bound to 192.168.1.101 -- renewal in 39656 seconds.

```

---

