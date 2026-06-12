---
title: "Connecting to wireless network, but not to internet"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by Nikkiru on 2009-11-20
I'm running 9.1, using an external wireless card.  As the thread title says, I can connect to the wireless network, but not to the internet. I'm posting this from the same network, only using windows.

I tried a ping using the google ip (74.125.79.99), but no luck. 

This is what I get from an iwconfig:
> nikkiru@ubuntu:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

wmaster1  no wireless extensions. 

wlan1     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1A:70:E0:52:8D   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=33/70  Signal level=-77 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 


As you can see, the second wireless card is connected. I don't know what the rest of the code means. 

This is what I get from an ip route list:
> 

nikkiru@ubuntu:~$ ip route list 
192.168.1.0/24 dev wlan1  proto kernel  scope link  src 192.168.1.100  metric 2 
169.254.0.0/16 dev wlan1  scope link  metric 1000 
default via 192.168.1.1 dev wlan1  proto static 

That's all I know to do from the terminal, and I don't really even know what most of it means.  Does it give a useful clue to the problem?

---

### Post by komputes on 2009-11-20
Well you are definitely connected to linksys and have an IP address. You should troubleshoot the router to make sure that it is in fact connected to your ISP. Go into the router and make sure it has an IP address from your ISP. Try using a cable, what is the result of that? Once you checked that you can move on to troubleshooting the wireless.

Are you able to connect to another (public) wifi? Is this the only access point which gives you trouble? 

If you think it may be the wireless (usb?) card, run "lsusb" and share the results.

What is the make and model of the external usb card?

---

### Post by Nikkiru on 2009-11-20
> **komputes said:**
> Well you are definitely connected to linksys and have an IP address. You should troubleshoot the router to make sure that it is in fact connected to your ISP./


As I think I said above, I'm posting from that same connection - just in windows.

> Are you able to connect to another (public) wifi? Is this the only access point which gives you trouble? 

It's the only wifi point I have access to, and it only gives me trouble in ubuntu.

---

### Post by gtstephenson on 2009-11-21
I have had that same trouble with my machine. I think there is a timing issue in the 9.1 code. What I have done is (after the wireless interface connects) run the command sudo ifdown wlan0 then sudo ifup wlan0. I then immediately have an internet connection.

Dunno exactly what's wrong but that works every time for me.

Tom Stephenson

---

### Post by Nikkiru on 2009-11-21
> **gtstephenson said:**
> I have had that same trouble with my machine. I think there is a timing issue in the 9.1 code. What I have done is (after the wireless interface connects) run the command sudo ifdown wlan0 then sudo ifup wlan0. I then immediately have an internet connection.

Dunno exactly what's wrong but that works every time for me.

Tom Stephenson

I tried your suggestion, but it didn't work for me. Here's a copy of the terminal session:

> nikkiru@ubuntu:~$ sudo ifdown wlan0 
ifdown: interface wlan0 not configured 
nikkiru@ubuntu:~$ sudo ifup wlan0 
Ignoring unknown interface wlan0=wlan0. 
nikkiru@ubuntu:~$ 

---

### Post by Lutin on 2009-11-21
Nikkiru

I have been having the same problem as you, and I have found a curious thing.

I noticed that you say that you are able to post having booted into windows, yes? Is your machine dual boot Ubuntu / windows?

After my laptop failed to connect, even though it said it was, I rebooted into windows. The connection was established, as shown by starting Firefox. I then shut down and booted back into Ubuntu Karmic and, hey Presto, my connection came up properly.

I have no idea why this should work, but it does for me,

---

### Post by Nikkiru on 2009-11-21
Every time I log into ubuntu, it's after having logged into XP and having established a connection. 

I keep seeing references to "karmic". What does that mean, specifically? How would that be different from logging into 9.1?

---

### Post by Palanthas on 2009-11-21
'fraid I can't help much on the wireless bit but about the Karmic reference...  9.10 is Karmic Koala. (as 9.04 was Jaunty Jackalope)

---

### Post by tlois on 2009-11-21
Have you tried hardwiring your laptop in Ubuntu to your router to see if it gets on the internet at all?

---

### Post by Nikkiru on 2009-11-21
> **tlois said:**
> Have you tried hardwiring your laptop in Ubuntu to your router to see if it gets on the internet at all?

Would if I could, but I can't. It's not my router.

---

### Post by Nikkiru on 2009-11-22
Still hoping somebody has an idea for me to try.

---

### Post by JafoFubar on 2009-11-22
I'm having the same problem. Go to System/Preferences/Network Connections, go to the Wireless tab, highlight the connection you want, click Edit and go to the IPv4 tab. On mine, when I connect, the Method is set to Shared to Other Computers. So I'm not getting a DHCP IP address and I'm not getting DNS settings. But it **is** connected to the router. When I change that setting to Automatic (DHCP), it then tries to connect and then a box pops up prompting me to enter my WEP key. I enter it but it won't connect. The box pops back up prompting me to enter my WEP key. I'm stuck at this point.

---

### Post by JafoFubar on 2009-11-22
OK. It's working now. I had to change it to DHCP automatic and then open Terminal and run **sudo dhclient** and it connects fine now. I rebooted a couple of times and it reconnects every time so I guess I'm done.

---

### Post by Nikkiru on 2009-11-23
> **JafoFubar said:**
> OK. It's working now. I had to change it to DHCP automatic and then open Terminal and run **sudo dhclient** and it connects fine now. I rebooted a couple of times and it reconnects every time so I guess I'm done.

Wow, that brought up a whole other problem. 

I opened a terminal and typed in "sudo dhclient". Then it prompted for a password, but the window didn't accept input from my keyboard. 

> nikkiru@ubuntu:~$ sudo dhclient 
[sudo] password for nikkiru: 

Guess that's a whole other thread, eh? Or am I doing something obviously wrong?

---

### Post by JafoFubar on 2009-11-24
I'm not sure if you're messing with me or not so I'll hope you're not and answer anyway. When you type your password in Terminal, it doesn't show anything but it is accepting the input. You're used to seeing ***** or something, but it doesn't show in Terminal like that. Just type your password and hit Enter.

---

### Post by Scooter_X on 2009-11-24
> **gtstephenson said:**
> I have had that same trouble with my machine. I think there is a timing issue in the 9.1 code. What I have done is (after the wireless interface connects) run the command sudo ifdown wlan0 then sudo ifup wlan0. I then immediately have an internet connection.

Dunno exactly what's wrong but that works every time for me.

Tom Stephenson

:D
Hey thanks for posting that. It worked for me. I'm going to try, obviously, but when you reboot, do you have to do that all over again? Or is it usually just once for you after installing ubuntu for the first time?

EDIT: Actually, for some reason, only google.com wanted to come up. Everything else didn't... I'm going to keep poking around... But thanks all the same.

---

### Post by Scooter_X on 2009-11-24
Darn. JafoFubar, yours didn't work for me either. I'll keep poking around some more...

---

### Post by dmizer on 2009-11-24
I suspect this is just a DNS issue.

Can you ping google by IP address? If so, just configure your DNS server entries for OpenDNS: [https://store.opendns.com/setup/operatingsystem/ubuntu](https://store.opendns.com/setup/operatingsystem/ubuntu)

---

### Post by JafoFubar on 2009-11-25
I agree that it's a DNS issue. More specifically though, it's a DHCP issue. If they're connecting to their router, as I was, but their network card is not set to DHCP, it won't work. Yes, they can set it manually but I don't think that's what they're looking for. I could be wrong.

---

### Post by Nikkiru on 2009-11-27
> **JafoFubar said:**
> OK. It's working now. I had to change it to DHCP automatic and then open Terminal and run **sudo dhclient** and it connects fine now. I rebooted a couple of times and it reconnects every time so I guess I'm done.

I was already set at Automatic. I did try running sudo dhclient, but it seems not to be recognizing the connection either. 

This is what I got the first time I ran it, while I was connected to the same server I'm posting this from:

> nikkiru@ubuntu:~$ sudo dhclient 
[sudo] password for nikkiru: 
Internet Systems Consortium DHCP Client V3.1.2 
Copyright 2004-2008 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

SIOCSIFFLAGS: No such file or directory 
SIOCSIFFLAGS: No such file or directory 
Listening on LPF/wlan0/00:90:4b:7e:b2:be 
Sending on   LPF/wlan0/00:90:4b:7e:b2:be 
Listening on LPF/eth0/00:11:43:47:68:59 
Sending on   LPF/eth0/00:11:43:47:68:59 
Listening on LPF/wlan1/00:e0:4c:03:bf:03 
Sending on   LPF/wlan1/00:e0:4c:03:bf:03 
Sending on   Socket/fallback 
receive_packet failed on wlan0: Network is down 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6 
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4 
send_packet: Network is down 
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 4 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 
send_packet: Network is down 
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 5 
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 
send_packet: Network is down 
DHCPOFFER of 192.168.1.100 from 192.168.1.1 
DHCPREQUEST of 192.168.1.100 on wlan1 to 255.255.255.255 port 67 
DHCPACK of 192.168.1.100 from 192.168.1.1 
bound to 192.168.1.100 -- renewal in 41781 seconds. 
nikkiru@ubuntu:~$ ^C 
nikkiru@ubuntu:~$ 

Then I rebooted to windows to make sure the connection was working. When I booted back into Karmic, and saw that I was showing a connection, I tried again. No connection through FF again, and sudo dhclient gave a somewhat different report:

> nikkiru@ubuntu:~$ sudo dhclient 
[sudo] password for nikkiru: 
Internet Systems Consortium DHCP Client V3.1.2 
Copyright 2004-2008 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
SIOCSIFFLAGS: No such file or directory 
SIOCSIFFLAGS: No such file or directory 
Listening on LPF/wlan0/00:90:4b:7e:b2:be 
Sending on   LPF/wlan0/00:90:4b:7e:b2:be 
Listening on LPF/eth0/00:11:43:47:68:59 
Sending on   LPF/eth0/00:11:43:47:68:59 
Listening on LPF/wlan1/00:e0:4c:03:bf:03 
Sending on   LPF/wlan1/00:e0:4c:03:bf:03 
Sending on   Socket/fallback 
DHCPREQUEST of 192.168.1.100 on wlan1 to 255.255.255.255 port 67 
receive_packet failed on wlan0: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4 
send_packet: Network is down 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 
send_packet: Network is down 
DHCPREQUEST of 192.168.1.100 on wlan1 to 255.255.255.255 port 67 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 
send_packet: Network is down 
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 6 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 
send_packet: Network is down 
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 12 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19 
send_packet: Network is down 
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 19 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 
send_packet: Network is down 
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4 
send_packet: Network is down 
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 16 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
nikkiru@ubuntu:~$ 

Given what I already posted on page 1, can anybody make heads or tails of this?

---

### Post by Nikkiru on 2009-11-28
bump

---

### Post by DirtyGTO on 2009-11-28
I'm having the same problem as well. I just setup Ubuntu on my Netbook and can't get it to receive a proper internet connection. This was a fresh install, first thing I did was setup the wireless. I found my router and established a connection, as far as I can tell everything is OK to start surfing the web. Firefox loads up to the home window fine, but when I try to go to another website it just sits there and loads. Nothing happens, just says "connecting to google.com" in the corner. 

I know it isn't the router. I have 3 other devices running from the same router, two wired and one wireless. Just before I installed Ubuntu, I had been online with the same Netbook with XP installed, so there should be absolutely no problem on the hardware end. The computer is now only Ubuntu.

---

### Post by dmizer on 2009-11-29
Please post the contents of:
```
/etc/network/interfaces
```

---

### Post by JafoFubar on 2009-11-29
> DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 
send_packet: Network is down 
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 5 
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 
send_packet: Network is down 
DHCPOFFER of 192.168.1.100 from 192.168.1.1 
DHCPREQUEST of 192.168.1.100 on wlan1 to 255.255.255.255 port 67 
DHCPACK of 192.168.1.100 from 192.168.1.1 
bound to 192.168.1.100 -- renewal in 41781 seconds. 
nikkiru@ubuntu:~$ ^C 
nikkiru@ubuntu:~$ You posted this earlier. Where it says DHCPACK, to me that means the router gave you an IP address....DHCP Acknowledge. Then just after that it should reload smb.conf but it looks like you hit Ctrl-C. Why did you stop it ? Anyway, if you run that again or if you know you are connected to the router, right click on the network icon on the top panel and click on Connection Information and see if there's an IP address and more importantly, a Primary DNS address. 

Also, someone asked you to try **sudo ifdown wlan0 then sudo ifup wlan0**. You did but going by what you've posted, you're using wlan1. So maybe retry that command with wlan1 instead.

---

### Post by Nikkiru on 2009-12-01
> **dmizer said:**
> Please post the contents of:
```
/etc/network/interfaces
```

Could you explain please? I couldn't find an "etc" tab in the top bar, and when I pasted this into a terminal all I got was "permission denied".  So I have no idea what you're asking here.

---

### Post by Nikkiru on 2009-12-01
> **JafoFubar said:**
> You posted this earlier. Where it says DHCPACK, to me that means the router gave you an IP address....DHCP Acknowledge. Then just after that it should reload smb.conf but it looks like you hit Ctrl-C. Why did you stop it ? 

I stopped it because as far as I could see it was just going around and around in an unproductive loop, saying the same incomprehensible things over and over. 


> Anyway, if you run that again or if you know you are connected to the router, right click on the network icon on the top panel and click on Connection Information and see if there's an IP address and more importantly, a Primary DNS address. 

I did, and it's yes to both questions. 

> Also, someone asked you to try **sudo ifdown wlan0 then sudo ifup wlan0**. You did but going by what you've posted, you're using wlan1. So maybe retry that command with wlan1 instead.

 You say I'm already using wlan1, and tell me to retry using wlan1 "instead"? 

This leaves me utterly confused. What am I missing?

---

### Post by dmizer on 2009-12-01
> **Nikkiru said:**
> Could you explain please? I couldn't find an "etc" tab in the top bar, and when I pasted this into a terminal all I got was "permission denied".  So I have no idea what you're asking here.

Run this command:
```
cat /etc/network/interfaces
```

Also, please post the results of this command:
```
ifconfig
```

And this (this is just pinging google by IP address):
```
ping -c 4 74.125.67.100
```

---

### Post by Nikkiru on 2009-12-01
Ubuntu isn't  connecting to the network tonight. It's detecting other networks in the neighborhood, but for some reason it's not picking up the one I'm on right now (using windows). 

Anyhow...> **dmizer said:**
> Run this command:
```
cat /etc/network/interfaces
```
I got:
> nikkiru@ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

> Also, please post the results of this command:
```
ifconfig
```

I got: 
> nikkiru@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:47:68:59  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan1     Link encap:Ethernet  HWaddr 00:e0:4c:03:bf:03  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster1  Link encap:UNSPEC  HWaddr 00-E0-4C-03-BF-03-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

> And this (this is just pinging google by IP address):
```
ping -c 4 74.125.67.100
```

As I said, I'm not connecting tonight. But I'm saving this thread, so I'll try this later.

Thanks.

---

### Post by ant2ne on 2009-12-01
You say "I'm not connecting" but you are connecting and getting an IP address from DHCP. Oddly 192.168.1.100 which is possible, but kind of odd. But, DHCP isn't the same as DNS. 

ping googles IP address

```
ping -c 4 74.125.67.100
```

then ping it by name

```
ping -c 4 www.google.com
```

having failed both of those, ping your gateway 

```
ping -c 4 192.168.1.1
```

but, You said that it isn't your router. So I wonder if you are "stealing" someones protected WAP and you are being filtered by mac address or you do not have the proper encryption key. I've seen wifi devices 'connect' to a WAP but not let you do anything.

---

