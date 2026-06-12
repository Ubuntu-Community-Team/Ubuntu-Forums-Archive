---
title: "only my home wireless doesn't work..?"
date: 2013-01-15
forum: Networking &amp; Wireless
---

### Post by mrjustusthomas on 2013-01-15
Okay! so I used the windows installer to dual boot ubuntu on my windows 7 notebook. everything works fine, but i've had wireless issues from the start. My home wireless network says it's connected, but I don't have access to the internet. I tried my neighbors wifi and my school's wifi and they work just fine. I'm a complete and total noob to linux so be gentle! thanks for the help.

sorry i know there are a ton of wireless issue threads but i've been searching for hours and i haven't found anything really similar to my problem :/

---

### Post by eenofonn on 2013-01-15
Could be you're not using the correct security settings for your wifi at home? e.g. you need to use WPA2-PSK and you're trying to use WPA

---

### Post by mrjustusthomas on 2013-01-15
Nope that part looks okay! i've tried changing up some of the settings and there's no difference

---

### Post by eenofonn on 2013-01-15
> **mrjustusthomas said:**
> Nope that part looks okay! i've tried changing up some of the settings and there's no difference
Sorry to hear that! I don't have that much experience with Wifi troubleshooting on Ubuntu but I thought I'd make an attempt at tier 1 support lol 

If you load a live cd does the wifi behave differently?

---

### Post by mrjustusthomas on 2013-01-15
I don't have a live CD and I don't have any CD's to install with.

---

### Post by eenofonn on 2013-01-15
> **mrjustusthomas said:**
> I don't have a live CD and I don't have any CD's to install with.
oh sorry... are the problems just related to ubuntu or does the wifi have issues in windows as well?

---

### Post by mrjustusthomas on 2013-01-16
everything is fine in windows, and the only issue i have in ubuntu is with my own home network. every other network i have tried works. so it's nothing with my router (windows and my phone connect fine), and it's not my laptop hardware because it connects to every other network. the only difference i've seen is all of the networks that have worked haven't had a password, but my home network does

---

### Post by eenofonn on 2013-01-16
> **mrjustusthomas said:**
> everything is fine in windows, and the only issue i have in ubuntu is with my own home network. every other network i have tried works. so it's nothing with my router (windows and my phone connect fine), and it's not my laptop hardware because it connects to every other network. the only difference i've seen is all of the networks that have worked haven't had a password, but my home network does
oh that is interesting lemme do some digging and see if I can find anything worth trying. What version of Ubuntu are you running and laptop specs etc

---

### Post by eenofonn on 2013-01-16
additionally this looks like it may be helpful

[Ubuntu Wireless Troubleshooting]("https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html")

---

### Post by mrjustusthomas on 2013-01-16
thanks so much! i'm running 12.10 on an asus x53e notebook, windows 7,4 gigs of ram, 2.1 GHz processor...

p.s. i'm using ubuntu right now with my neighbors wifi and everything seems to be working normally

---

### Post by eenofonn on 2013-01-16
does it keep asking you for a password or does it take the password and then does nothing after that

---

### Post by mrjustusthomas on 2013-01-16
it takes the password and when i connect it will sometimes randomly disconnect. i've deleted the connection and retyped the password like 15 times :P also none of the stuff on the trouble shooting guide worked

---

### Post by eenofonn on 2013-01-16
ok so when it takes the password does the connection work even for a little while?

---

### Post by mrjustusthomas on 2013-01-16
no if you try to load a webpage it crashes and says to try reloading. and it's not just the browser because no system features can connect. It says DNS lookup failed

---

### Post by mrjustusthomas on 2013-01-16
Should I just try un installing and reinstalling ubuntu?

---

### Post by eenofonn on 2013-01-16
might not be the worst idea but if you haven't really made any modifications to the system then it might do nothing for you

After you enter the password for the wireless can you open a terminal and post the output of ifconfig

---

### Post by mrjustusthomas on 2013-01-16
root@ubuntu:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 10:bf:48:23:8f:b2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:29902 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29902 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2641650 (2.6 MB)  TX bytes:2641650 (2.6 MB)

wlan0     Link encap:Ethernet  HWaddr 44:6d:57:96:00:dc  
          inet addr:10.0.0.16  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::466d:57ff:fe96:dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:193495 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86383 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:233229133 (233.2 MB)  TX bytes:12573522 (12.5 MB)

---

### Post by eenofonn on 2013-01-16
is 10.0.0.16 a proper ip for your wifi?

looks like you've got an ip but no gateway

how about the ifconfig when connected to another network? does that show a gateway?

---

### Post by mrjustusthomas on 2013-01-16
on my android phone it says the IP of HOME-A6F2 is 10.0.0.4...or maybe that's my phone's ip? i don't think so? here's the ifconfig for my neighbors wifi

root@ubuntu:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 10:bf:48:23:8f:b2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:33128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2919788 (2.9 MB)  TX bytes:2919788 (2.9 MB)

wlan0     Link encap:Ethernet  HWaddr 44:6d:57:96:00:dc  
          inet addr:192.168.1.125  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::466d:57ff:fe96:dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:196360 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89408 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:234500393 (234.5 MB)  TX bytes:13129695 (13.1 MB)

---

### Post by eenofonn on 2013-01-16
ok so it looks like you're connecting to your router and getting a dhcp lease can you ping 10.0.0.1 and get a reply when connected to your wifi?

---

### Post by mrjustusthomas on 2013-01-16
no reply

---

### Post by eenofonn on 2013-01-16
hrmph ok lemme do some googling, sorry if I'm taking too long to get back to you I'm trying to help a few other people at the same time

---

### Post by mrjustusthomas on 2013-01-16
no worries man i'm grateful for the help! :D

---

### Post by eenofonn on 2013-01-16
just for curiosity sake what does this give you

sudo iwlist wlan0 scan

---

### Post by eenofonn on 2013-01-16
and yet another link for you to try

[Ubuntu Wireless Troubleshooting -  Ubuntugeek]("http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html")

---

