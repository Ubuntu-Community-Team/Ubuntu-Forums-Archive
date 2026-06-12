---
title: "slow wired connection"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by latenightrob on 2010-01-15
Just finished setting up a dual boot with win7 and ubuntu 9.10 on a new HP laptop, all is well except for one thing.  I noticed that when I plug in the laptop to the wired connection it is very slow to download anything, (wireless is very much faster)

any ideas what to do?

thanks

---

### Post by latenightrob on 2010-01-15
update using speedtest.com 

wired download speed 3.4mb/s  
upload was fine 4.1 mb/s

wireless download   19.78mb/s
upload              4.4mb/s

---

### Post by superprash2003 on 2010-01-15
post output of
1)ifconfig
2)iwconfig
  you could try disabling ipv6 for the wired interface [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by Iowan on 2010-01-16
You can see if the DNS servers are the same in both cases (*/etc/resolv.conf*). MTU can affect throughput (**ifconfig** will reveal this value).

---

### Post by latenightrob on 2010-01-18
I booted into windows and did the speed test as well and it too was slow.  I went to HP website and updated or re-installed the Ethernet and it fixed the problem in windows but in ubuntu still really slow.  here is the ifconfig output

 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:9e:3c:41:ad  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:9eff:fe3c:41ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27279 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35826470 (35.8 MB)  TX bytes:4929519 (4.9 MB)
          Interrupt:30 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

Thanks for the help
Rob

---

### Post by latenightrob on 2010-01-18
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by latenightrob on 2010-01-18
anyone?

---

### Post by Iowan on 2010-01-18
[This]("http://ubuntuforums.org/showthread.php?t=1376506") thread goes through some MTU checks. 
[Here]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4") is a help page on slow browsing (though it's getting dated).

---

