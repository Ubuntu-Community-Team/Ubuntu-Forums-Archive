---
title: "No network access due to WLAN0:AVAHI"
date: 2011-07-24
forum: Networking &amp; Wireless
---

### Post by Chenxicali on 2011-07-24
I have a laptop with Ubuntu 11.04. Failed to connect my home wireless network, which is composed of a modem and a Netgear router. 

---------------------
ifconfig showing:

wlan0     Link encap:Ethernet  HWaddr 00:24:d6:07:2b:a2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:30238 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24005 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26945081 (26.9 MB)  TX bytes:3169731 (3.1 MB)


wlan0:avahi Link encap:Ethernet  HWaddr 00:24:d6:07:2b:a2  
          inet addr:169.254.6.188  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

---------------------------------------------

iwconfig showing :

wlan0     IEEE 802.11abgn  ESSID:"mywirelessnetwork"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
================================

I do not quite understand how the virtual interface wlan0:avahi appeared. My guess was, my request "sudo dhclient wlan0" failed to get a valid ip, although I did not get any error message from running that command. I executed "sudo dhclient wlan0" again, but still no error message or network connection.

Later today, I tried to connect to a public wireless network. Still got the same error. But when I reboot my machine, no such problems.

I am confused by the wired situations. Is there anything wrong with my network configuration? What should I do if I encounter similar problems in future? 

Thanks in advance!

---

### Post by chili555 on 2011-07-25
When you get an avahi entry and a 169.xx IP adress, that's simply a placeholder for a real, working IP address. It  simply means that the computer tried but failed to be issued an IP address by the router or other access point. It could be:> my request "sudo dhclient wlan0" failed to get a valid ipIf Network Manager is installed and running, manual methods almost never work. NM has a firm grip on networking and won't relinquish control to usual manual methods. Is NM installed and running? When you click the icon, do you see your network? Does it try to connect?

---

### Post by Chenxicali on 2011-07-25
Thanks for your reply.

Sorry that I forgot to mention that I uninstalled NM and installed wicd instead. 

Is it possible that wicd caused the problem. But when I ran "sudo dhclient wlan0", wicd was not running. And my etc/network/interfaces showing "auto lo
iface lo inet loopback". Then I do not understand how wicd made my getting ip failed.

I wonder whether I need to do some pre-connection work. Like putting wlan0 down and then up to clean up environment?

---

### Post by chili555 on 2011-07-25
> Is it possible that wicd caused the problem.I doubt it. If evrything is working as expected, in my experience, Wicd works as well as NM and vice-versa.

When you click the Wicd icon, does it see your network? Does it try to connect? Is your network set up for WPA and WPA2 mixed mode? That is sometimes troublesome. I'd suggest WPA2 only, not mixed mode.

---

### Post by Chenxicali on 2011-07-25
> **chili555 said:**
> When you click the Wicd icon, does it see your network? Does it try to connect? Is your network set up for WPA and WPA2 mixed mode? That is sometimes troublesome. I'd suggest WPA2 only, not mixed mode.

Yes, wicd saw my network when I clicked it. It did not try to connect because I did not toggle "Automatically connect...". My network uses WEP because my roommate desktop can only connect to WEP encrypted network (a little bit wired).

Hinted by your suggestion, I found out that if I killed dhclient before network connection from cli, then my connection was set up successfully. I guess is, when stop dhclient process, the ip address is also released? Then dhcp server can then assign a new ip to my laptop?

---

### Post by chili555 on 2011-07-25
Ah, haaa! I believe that somewhere in the Wicd preferences, you can select dhcpd instead of dhclient. Please try it and let us know.

[http://wicd.net/punbb/viewtopic.php?id=733](http://wicd.net/punbb/viewtopic.php?id=733)

---

