---
title: "download speed  very slow"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by milio1401 on 2009-02-15
Hi people this is my first post,i'm relatively new to ubuntu,i just installed ubuntu 8.10 the 64-bit version like  a month and a half ago,i was using vista ultimate 64-bit,anyway,my problem is the when i try to download  a file the download speed is so very slow,when i first installed ubuntu  my speed was fine,then eventually it just  started getting slower and slower,amd now  it get to the point to download at 2 kbps,when i'm supposed to download at around at least when  i was using vista at 175 kbps :confused:i always go to forums and read a lot before asking anything  that's  how i set up my computer,and now this happens  and i don;t know what to do,by the way i have a DSL internet connection the wired kind,i did this i don't know if it was OK but i  found it in this thread

[http://www.chrisamiller.com/blog/2008/11/26/slow-internet-on-ubuntu-810/](http://www.chrisamiller.com/blog/2008/11/26/slow-internet-on-ubuntu-810/)

and it happens almost always just when i download  a file,because  when i'm surffing the web or watching a video it kinda freezes because of it but is  a little faster.
Anyway i'll be waiting for your reply thanks :(

---

### Post by graysky on 2009-02-15
Run a cable modem speed test under Ubuntu and under whatever OS.  Are they the same?

---

### Post by superprash2003 on 2009-02-15
go to the terminal and type **ifconfig** and post output here .. you could try disabling ipv6 , it could improve speeds [http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html](http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html)

---

### Post by milio1401 on 2009-02-16
OK  i was going to post my reply this morning but  i had to do something else,anyway the ifconfig command gave me this:

:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8d:b6:7e:eb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:50:8d:b6:7e:ec  
          inet addr:70.240.115.113  Bcast:70.240.115.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:569697 errors:0 dropped:0 overruns:0 frame:0
          TX packets:429787 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:819693763 (819.6 MB)  TX bytes:30226662 (30.2 MB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10980 (10.9 KB)  TX bytes:10980 (10.9 KB



And my modem speed is Download Speed: 1338 kbps 167.3 KB/sec 
Upload Speed: 326 kbps 40.8 KB/sec   according to this website
[http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/)

Well let me tell you what happened after disabling ipv6,it kind of improved my download speed now or at least sometimes let me tell you why i say sometimes,i downloaded the big files each one of them  was like 160 mb,when i downloaded the first one my download speed was like 115 kbps sometimes  a little more sometimes a little less,the second time i tried to download a file from rapidshare my download speed was 12 kbps,the third time i was downloading at around 115 kbps,and  i the computer where i had installed vista 64 in is the same where i installed ubuntu 64-bit 8.10 ,i didn't create a partition for vista i just erased it,i'm not using it anymore ,besides i like ubuntu better,it's safer,faster  i think ,more complicated but i don't mind

---

