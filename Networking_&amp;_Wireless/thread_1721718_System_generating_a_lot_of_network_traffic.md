---
title: "System generating a lot of network traffic"
date: 2011-04-04
forum: Networking &amp; Wireless
---

### Post by calif99x on 2011-04-04
Hi:

I have an odd problem that seems to have cropped up in the last few days; not clear yet as to the reason.  

Background:  I am running Ubuntu 10.10, upgraded a few weeks ago from 10.04.

I noted from the system monitor that the system was generating a lot of network traffic, on the order of 10Mbps if the information is correct (using system monitor and iftop).

From the process table, it appears that smbd is accumulating a lot of CPU time, which sort of makes sense as I use Samba for printing from a Windows 7 laptop.  But the traffic seems to be making a round trip as I just rebooted the system and it reports in about 10 minutes of uptime 1.2GB was send and 1.2GB was received.:confused:  Laptop is used for work, it is sitting idle for the last 30 minutes (VPN connection, etc); no backup or other interaction with the Ubuntu system.

Any thoughts on what causes this; how to find the problem process and the fix?

Thanks
Sandeep

---

### Post by conradin on 2011-04-04
well, thats interesting. first, lets make sure your firewall is on
```
 sudo ufw enable
sudo ufw default deny

```
then, it might be interesting to look at the logs, so youll need to enable logging,
```
 sudo ufw logging on
```

soo, actually theres a lot od different thing which could be going on. Do you get the same huge amount of traffic independent of the network you are on? A bad network port can generate tons of packet errors. Alternatively, you may be receiving broadcast and synch packets from other computers. And if some user on you network has been hacked, they they might be sending everyone a ton of packets.

to see what your computer is sending doing type:
```
 sudo netstat -anp |less 
```
there you'll see your active connections
alternatively you could try using wire-shark to capture and analyze your packet traffic.
another nice traffic monitor is iptraf you can sudo apt-get install it then use
```
iptraf –d eth0

```
to get an idea whats coming and whats going on your system.
give that a try, see what you can find and get back to us.

---

### Post by calif99x on 2011-04-06
OK, tried the suggestions, I do need some help in interpretting what I am seeing.

The IPtraf shows an incoming rate 12701 kbits/ sec and an outgoing rate of 12146 kbits / set.  This matches iftop showing about 12Mb going back and forth to the IP address for the laptop.  The total packet count is pretty much just a blur witm Incoming and Outgoing counts in the 1800M+ range already and both ticking over about 1M per second.

The laptop & Ubuntu box are both plugged into the same gigabit switch, the port light are going like crazy.  On the plus side, by router is pretty quite suggesting the traffic and activity are both entirely local.

Not sure where ufw is putting the log, or more specifically what triggered the data swapping.

The situation sort of reminds me of the old email situation where two people set out of office notices and the system keeps bouncing emails replies back and forth till the storage fills up and crashes.

I have installed wireshark but do not have experience using it.  Other information of note is that smbd is using 12% of the CPU and is the highest load process, next if firefox at 2%; CPU time for smbd is also going up steadily.

Thanks
Sandeep

---

### Post by calif99x on 2011-04-06
A quick note; I just took another look at the system and the traffic appears to be back to normal.

I found the ufw.log file, doing a tail gives:
Apr  6 11:05:34 homeserv kernel: [12157.332820] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:d1:eb:3d:40:00:21:70:97:56:ba:08:00 SRC=192.168.1.100 DST=192.168.1.102 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9032 DF PROTO=UDP SPT=61809 DPT=161 LEN=86 
Apr  6 11:06:13 homeserv kernel: [12196.351680] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:d1:eb:3d:40:00:21:70:97:56:ba:08:00 SRC=192.168.1.100 DST=192.168.1.102 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8961 DF PROTO=UDP SPT=61809 DPT=161 LEN=86 
Apr  6 11:06:24 homeserv kernel: [12207.019613] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:d1:eb:3d:40:00:21:70:97:56:ba:08:00 SRC=192.168.1.100 DST=192.168.1.102 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=26543 DF PROTO=UDP SPT=61809 DPT=161 LEN=86 
Apr  6 11:06:34 homeserv kernel: [12217.159180] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:d1:eb:3d:40:00:21:70:97:56:ba:08:00 SRC=192.168.1.100 DST=192.168.1.102 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10497 DF PROTO=UDP SPT=61809 DPT=161 LEN=86 
Apr  6 11:07:13 homeserv kernel: [12256.692241] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:d1:eb:3d:40:00:21:70:97:56:ba:08:00 SRC=192.168.1.100 DST=192.168.1.102 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9823 DF PROTO=UDP SPT=61809 DPT=161 LEN=86 
Apr  6 11:07:23 homeserv kernel: [12266.892302] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:d1:eb:3d:40:00:21:70:97:56:ba:08:00 SRC=192.168.1.100 DST=192.168.1.102 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=26688 DF PROTO=UDP SPT=61809 DPT=161 LEN=86 
Apr  6 11:07:34 homeserv kernel: [12277.033595] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:d1:eb:3d:40:00:21:70:97:56:ba:08:00 SRC=192.168.1.100 DST=192.168.1.102 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10817 DF PROTO=UDP SPT=61809 DPT=161 LEN=86

---

### Post by Billsputters on 2011-04-06
I am getting exactly the same, about 12k of traffic. Seems to be a lot going to the time servers, at least they pop up quite a lot.

---

### Post by calif99x on 2011-04-06
I suspect and blame my Windows 7 unit; well because the problem did not happen before and the traffic seems to be some form of tennis between the two systems :lolflag:

Not going outside means that my broadband provide does not shut me down.

Cheers
Sandeep

---

### Post by calif99x on 2011-04-30
I am still getting the same problem.  Any ideas of how to track down what is causing this on the Windows side?

Thanks
Sandeep

---

### Post by dongeorgem on 2012-12-19
I have the same problem too. it associated with UPNP. Wireshark reports that the traffic is being directed to port 2869 on the Windows PC. The port keeps changing randomly on the linux machine so I couldn't trace the originating application.

My solution was to use the Windows Firewall and block all incoming traffic to port 2869, then on the Ubuntu Firewall as extra precaution, I blocked all traffic outbound to port 2869. This caused all the traffic to stop and the network went quiet. Now am at 0Kbps when Idle on both computers.

Using the firewall seems to work.

sudo ufw deny out to [Windows IP Address] port 2869

or 

sudo ufw deny out to any port 2869

---

