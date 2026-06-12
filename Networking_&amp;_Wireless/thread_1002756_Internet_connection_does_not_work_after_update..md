---
title: "Internet connection does not work after update."
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by zoeken on 2008-12-05
After 3 days of reading threads around here without any success i#ve decided to post a new thread.

Problem sounds like that:

I'm new ubunutu user, but i was happy with it for the last 6 months. Three days ago Update Manager asked for update. After update my network go crazy. When i start the computer i have network up and running but no internet. After some restarts (sometimes after one other times after more than one) everything is ok. 
I've heard that problem can be from Network Manager, so ihave removed it and now i have Wicd. It's a little better because now from 10 starts i have only 2 ... 4 internet failure, before was very hard to get to the internet.
The system spec. are: Ubuntu HH 8.04 LTS on CPU AMD X2 3800+ with 2 Gb RAM, on board network RTL8111.

ifconfig output:
eth0      Link encap:Ethernet  HWaddr 00:19:66:29:34:f7  
          inet addr:82.212.12.175  Bcast:82.212.13.255  Mask:255.255.254.0
          inet6 addr: fe80::219:66ff:fe29:34f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:140638 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4905 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14642194 (13.9 MB)  TX bytes:578583 (565.0 KB)
          Interrupt:251 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4401 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4401 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:178485 (174.3 KB)  TX bytes:178485 (174.3 KB)

The output from ifconfig command it's the same in both situation - internet works or it' not working. The only thing it changes is the IP. Internet connection it is made through a Cable Modem without a router. 
If helps.... when i use the live DVD with Ubuntu internet works every time, so i believe it is not a hardware problem, but i don't want to reinstall Ubuntu again... it must be a solution! Anyone can help???


Regards!

---

### Post by dollylamb on 2008-12-05
try to ping your gateway then somewhere. If it works, i guess there's something wrong with your dns resolver.

---

### Post by superprash2003 on 2008-12-05
post output of cat /etc/resolv.conf and type ping google.com and post output

---

### Post by zoeken on 2008-12-05
thanks for quick reply!

steve@steve-desktop:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

steve@steve-desktop:~$ ping 72.14.205.100
PING 72.14.205.100 (72.14.205.100) 56(84) bytes of data. ---- it seems that is the Ip for google.com
ping: sendmsg: Operation not permitted

cat /etc/resolv.conf   -  i suppose i have to try this when the internet does not work...Now the result is:
steve@steve-desktop:~$ cat /etc/resolv.conf
nameserver 91.89.89.91
nameserver 91.89.91.94

So that's the result from ping. In the latest 2 hours i have tried to manually set up the IP. It works great but i have dynamic IP so when my cable modem get another IP it is stop working. Now i'm testing another thing - only with DNS manually inserted. It works but i don't know for how many restart. Now i'm on the 5'th restart without any problem.

---

### Post by zoeken on 2008-12-07
From today on i'm a happy man = PROBLEM SOLVED!
Solution:

[https://help.ubuntu.com/8.04/internet/C/troubleshooting.html#troubleshooting-ipv6]("https://help.ubuntu.com/8.04/internet/C/troubleshooting.html#troubleshooting-ipv6")

IPv6 Not Supported

   1.IPv6 is supported by default in Ubuntu and can sometimes cause problems.
   2.To disable it, open a Terminal (Applications &#8594; Accessories &#8594; Terminal) and type the command: [COLOR="DarkRed"]gksudo gedit /etc/modprobe.d/aliases[/COLOR]
   3.Find the line [COLOR="DarkRed"]alias net-pf-10 ipv6[/COLOR] and change it to read [COLOR="DarkRed"]alias net-pf-10 off[/COLOR].
   4.Reboot Ubuntu.



Yeah.... 
Problem com out again after ~20 good starts.....
I'm doomed! .... agian.....

---

