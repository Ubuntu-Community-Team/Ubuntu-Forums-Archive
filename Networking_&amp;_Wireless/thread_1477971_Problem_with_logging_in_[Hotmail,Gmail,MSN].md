---
title: "Problem with logging in [Hotmail,Gmail,MSN]"
date: 2010-05-09
forum: Networking &amp; Wireless
---

### Post by Axlswe on 2010-05-09
Greetings, this is my first post on the board!

I tried to post this on a Swedish ubuntu forum but it seems like noone there is able to help me with my problem.

The problem in short: I have two laptops, both with Ubuntu 10.04 Lucid installed, both connected to the same wireless router (Netgear 54mbit). One of my laptops (eee 901go) runs Lucid flawlessly, but the other one (Toshiba, pretty old) has trouble logging in to Hotmail, Gmail and my MSN (through Empathy, my msn id is a hotmail). By trouble I mean that after entering my login information, my browser (Firefox) tries to connect to the log in server for a while, then displays an connection error message. Worth nothing is that the laptop with this problem also has a weaker connection to the wireless lan than my eee, and takes longer to display websites as well.

Wireless card: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

Iwconfig:
IEEE 802.11bg  ESSID:"steaxe"  
Mode:Managed   Frequency:2.462 GHz  Access Point: 00:1E:2A:52:91:7A   
Bit Rate=1  Mb/s   Tx-Power=20 dBm   
Retry  long limit:7   RTS thr:off    Fragment thr:off
Power Management:off
Link Quality=51/70  Signal  level=-59 dBm  
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid  frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Please note that I'm not very well versed with Linux distributions. ;)

I've tried to disable IPV6 settings in firefox, since that seems like a common problem with slow website displays, but that didn't solve my problem. My uneducated guess would be that there is something wrong with my wireless card, the drivers or something like that. Anyway if you have any idea of what is going on, please let me know.

[Edit]: Smilies in text.

---

### Post by Iowan on 2010-05-09
This is becoming one of my "stock" answers - and doesn't always (usually?) help, but you can check [MTU]("http://ubuntuforums.org/showthread.php?t=1376506") (post #15).

---

### Post by Axlswe on 2010-05-09
Thanks for the quick response! I think we're on to something here. I had the exact same results of the pings as the guy in the thread you linked to, so I just followed the steps described there and when I set the MTU to 1492 I could log in to Hotmail and my MSN. But the joy didn't last long for as soon as I restarted my computer the problem reappeared. I checked with ifconfig | grep MTU and the mtu was still set to 1492, but I couldn't log in to msn / hotmail and I couldn't even load ubuntuforums.com. So I tried the whole ping process again and this time 1492 gave me an error, so I lowered the number and somewhere at around 1460 it gave me the other reply. So I set MTU to 1460, but no dice. Pinged again and I got the error message all the way down to 1430 this time. Same process, no dice. I'm most likely doing something wrong here... But as I managed to log in ONCE, we have to be on the right track, don't you think?

(I had to boot xp to post this message since ubuntu has trouble loading the thread.)

> ping 192.168.2.1 -c 1 -s 1499 -M do
PING 192.168.2.1 (192.168.2.1) 1499(1527) bytes of data.
From 192.168.1.2 icmp_seq=1 Frag needed and DF set (mtu = 1500)

--- 192.168.2.1 ping statistics ---
0 packets transmitted, 0 received, +1 errors

192.168.2.1 -c 1 -s 1480 -M do
PING 192.168.2.1 (192.168.2.1) 1480(1508) bytes of data.
From 192.168.1.2 icmp_seq=1 Frag needed and DF set (mtu = 1500)

--- 192.168.2.1 ping statistics ---
0 packets transmitted, 0 received, +1 errors

ping 192.168.2.1 -c 1 -s 1473 -M do
PING 192.168.2.1 (192.168.2.1) 1473(1501) bytes of data.
From 192.168.1.2 icmp_seq=1 Frag needed and DF set (mtu = 1500)

--- 192.168.2.1 ping statistics ---
0 packets transmitted, 0 received, +1 errors


ping 192.168.2.1 -c 1 -s 1472 -M do
PING 192.168.2.1 (192.168.2.1) 1472(1500) bytes of data.

--- 192.168.2.1 ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms

ping [www.cisco.com]("http://www.cisco.com") -c 1 -s 1472 -M do
PING origin-www.cisco.com (72.163.4.161) 1472(1500) bytes of data.

--- origin-www.cisco.com ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms

ping [www.cisco.com]("http://www.cisco.com") -c 1 -s 1464 -M do
PING origin-www.cisco.com (72.163.4.161) 1464(1492) bytes of data.
1472 bytes from www1.cisco.com (72.163.4.161): icmp_seq=1 ttl=110 time=186 ms

--- origin-www.cisco.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 186.642/186.642/186.642/0.000 ms

ping 72.163.4.161 -c 1 -s 1472 -M do
PING 72.163.4.161 (72.163.4.161) 1472(1500) bytes of data.

--- 72.163.4.161 ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms

ping 72.163.4.161 -c 1 -s 1464 -M do
PING 72.163.4.161 (72.163.4.161) 1464(1492) bytes of data.
1472 bytes from 72.163.4.161: icmp_seq=1 ttl=110 time=188 ms

--- 72.163.4.161 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 188.972/188.972/188.972/0.000 ms

ifconfig | grep MTU
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

sudo ifconfig wlan0 mtu 1492

ifconfig | grep MTU
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1

cat /etc/network/interfaces
auto lo
iface lo inet loopback


---

### Post by Axlswe on 2010-05-10
Any idea what I'm doing wrong here? The mtu dropping lower everytime I check seems kind of fishy? But then again I don't know how the mtu works, or even what it is :P

---

### Post by searchesend on 2010-05-12
I have the same Atheros Wireless on a Toshiba L30-11D and the same issue with loading pages/accessing hotmail or gmail

---

### Post by Axlswe on 2010-05-13
Oh, I got a L30-105, have you tried the MTU thing Iowan mentioned?

---

### Post by searchesend on 2010-05-13
I tried lowering the MTU and it didn't help me. I have fixed mine by installing the madwifi driver using this thread;
[http://www.ge.ubuntuforums.org/showthread.php?t=1163380&highlight=ar2413](http://www.ge.ubuntuforums.org/showthread.php?t=1163380&highlight=ar2413)
I'm not sure if this is the proper way of doing it because I don't know anything about computers but it's worked OK for me.

---

### Post by Axlswe on 2010-05-13
Thanks for the tip man, I'll try it out.

---

### Post by Axlswe on 2010-05-13
I just swapped drivers myself and now it's working! Awsome, thanks a lot for the tip =D>
Mods can mark this solved (I can't seem to figure out if I can do it myself).

---

### Post by lisati on 2010-05-13
> **Axlswe said:**
> I just swapped drivers myself and now it's working! Awsome, thanks a lot for the tip =D>
Mods can mark this solved (I can't seem to figure out if I can do it myself).

Click on "Thread tools" at the top of the thread, then "Mark thread as 'solved'"

---

