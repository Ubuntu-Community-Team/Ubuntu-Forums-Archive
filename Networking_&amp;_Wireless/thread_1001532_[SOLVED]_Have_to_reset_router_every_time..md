---
title: "[SOLVED] Have to reset router every time."
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by riplox on 2008-12-04
Ok. I'm new to Ubuntu, but figured it would be more proper to post here rather than the newbie board. I don't really know any terminal commands, but I'll explain what's happening with my laptop.

I recently installed Ubuntu 8.10 on my Dell 600m, and couldn't get my wireless connection to work properly. If I reset my router, I get connection and everything works fine (wired has always worked, so no problem there). However, every time I restart the laptop, the problem reappears and I have to reset my router to get a wireless connection again. What is going on? No other computer (or my wifi phone) has this problem. Of course, none of the other computers run Ubuntu either. I've been scouring the internet for days now (maybe a couple of weeks actually) and haven't found anything solid. This is really annoying me! Please help.

---

### Post by gTinker on 2008-12-04
From the symptoms you describe, I would suspect that your system is not asking for an IP address from the routers DHCP server and that resetting the router forces that. But that is just a guess without more data.

In a terminal, type cat /etc/network/interfaces and post the results here to give us some more information. The results of sudo ifconfig might also be helpful. 

Sudo dhclient might be a good test but it would still be a good idea to furnish the results.

---

### Post by superprash2003 on 2008-12-04
sudo not required for ifconfig.. are you able to ping your router when disconnected?

---

### Post by razy60 on 2008-12-04
your laptop may be remembering the IP address from an earlier session, so when you switch of it disconnects which allows another PC to use that address. The router may not be set to remember IP addresses of a specific PC so it just reassigns the address to the next PC to connect.
 when you reconnect your laptop wants to connect using its remembered IP but it cant as its been used elsewhere, when you reboot your router the pc with preassigned IP's get there addresses first, which is why you can connect.
Either set your router to keep addresses or try to get your laptop to automatically reassign its address.
Or I'm completely barking up the wrong tree:p

Raz

---

### Post by riplox on 2008-12-08
Sorry it's taken me a while to get back to this.

**WHILE CONNECTED**
josh@josh-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

josh@josh-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:56:74:61:bb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:04:23:6a:77:13  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:130 errors:592 dropped:592 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9306 (9.3 KB)  TX bytes:6836 (6.8 KB)
          Interrupt:5 Base address:0x8000 Memory:fafef000-fafeffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**WHILE DISCONNECTED**
josh@josh-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:56:74:61:bb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:04:23:6a:77:13  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:589 dropped:589 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:612 (612.0 B)  TX bytes:3496 (3.4 KB)
          Interrupt:5 Base address:0x8000 Memory:fafef000-fafeffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by riplox on 2008-12-09
Ok. I'm experiencing a new problem now. Intermittent disconnects. It reconnects just after and the signal strength is fine, I'm on channel 11 too, so it's not interfering with other wireless stuff in the area. What's going on? What can I do to give you information so I can get this worked out?

---

### Post by bab1 on 2008-12-09
I'm just starting to learn about the nm-applet (Network Manager).  This sounds more like laptop's problem rather than the router.  See [[COLOR="Blue"]**here**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1004752") for the link to a great article on how Network Manager works and some insight into use the gconf editor.

---

### Post by riplox on 2008-12-09
Thanks for the article, pretty informing. But I don't really understand linux all that much. I just kind of dove in from years of working in Windows, so it wasn't really all that helpful. Don't get me wrong, I understand it mostly, but the core understanding of Linux is holding me back.

---

### Post by bab1 on 2008-12-09
Yes, It can be hard in the beginning.  But any insight is better than "not a clue".  I think if you configure your settings properly in NM you should be ok.

---

### Post by riplox on 2008-12-14
I figured out what was wrong. Apparently the card I have doesn't do WPA2 very well. I switched the router to plain ol' WPA and no problems. Durrr...

But now, I'm giving my laptop to my dad before he goes to work overseas, so I had to put Windoze back on so he can use the laptop while he's over there (military contract will be for a year or more). Oh well, at least I figured it out before he left.

---

