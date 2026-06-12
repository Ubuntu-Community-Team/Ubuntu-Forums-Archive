---
title: "Wireless only works when unsecured."
date: 2010-02-01
forum: Networking &amp; Wireless
---

### Post by jonjmill on 2010-02-01
I am having an issue with a newly installed 9.10 version of Unbuntu.  After a bit of fiddling about, I have found that the only way I can connect to my wireless network is if I unsecure the network.  Is there any explaination for why it will not work with either WEP or WPA?

---

### Post by quixote on 2010-02-03
Check in synaptic to see whether wpasupplicant is installed.  If not, install it. And hopefully that'll solve the problem.  (Although WEP should be working without it, so this probably isn't the whole problem.)  Come back and tell us what error messages you get.  

Also, run the following: ```
$ifconfig

$sudo iwlist scan
```and copy the output to your answer.  (Select on the terminal, and use ctrl-**shift**-c to copy, ordinary ctrl-v to paste the data in here.)

---

### Post by jonjmill on 2010-02-03
It was installed according to the package manager.  Here is the other info.



jonjmill@jonjmill-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:e9:bd:c9:16  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:16:01:56:02:9b  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:1ff:fe56:29b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:547 errors:0 dropped:0 overruns:0 frame:0
          TX packets:448 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:461459 (461.4 KB)  TX bytes:81735 (81.7 KB)
          Interrupt:18 Memory:feafe000-feb00000 

jonjmill@jonjmill-desktop:~$ C

jonjmill@jonjmill-desktop:~$ sudo iwlist scan
[sudo] password for jonjmill: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:F0:E8:C1:97
                    ESSID:"Lake Lemon House"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:45/100  Signal level:-67 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

jonjmill@jonjmill-desktop:~$

---

### Post by quixote on 2010-02-06
Sorry it took me so long to get back on this. 

There's a lot (*a lot*) I don't know about networking, but the ifconfig data looks pretty normal.  So it (may be) running okay at that level.  The iwlist, though, has two lines which, if I remember right, would conflict the way you have them: > "Mode:Managed" and "Encryption key:Off

I assume you have encryption off so you can use it.  But when encryption is on, I think mode needs to be "master".  When I had wireless issues, I used this forum post a lot: [howto wireless security]("http://ubuntuforums.org/showthread.php?t=318539").  There's a lot there, and unfortunately he stopped updating a couple of years ago, but at the command line level at lot of the stuff is much the same.  Anyway, there might be info there that helps you to get it working.

Another thing that's not so good is this: Quality:45/100 Signal level:-67 dBm Noise level:-96 dBm.  That's a rather low signal to noise ratio, and may be part of the reason it's not working encrypted.  The handshakes have to be a lot faster and cleaner for encryption to work.

Another alternative some people have used is a program called "wicd" which you can install via synaptic instead of the default nm-applet.  (I believe you have to add a repository to do it.)  Personally, I didn't like it and it didn't work for me, but lots of people swear by it, or did a couple of years ago.  I haven't kept up with how wicd is doing.

I hope any of this helps!

---

### Post by spegru on 2010-02-07
I doubt there is anything wrong with your Ubuntu 9.10 setup ........ unless you broke something fiddling!

On the other hand there could be a hardware problem. I saw an old IBM thinkpad that did something similar - No security & wep were ok, but no use on WPA. It turned out the old wifi card did not support wpa. I fixed that by changing the mini pci internal wifi card for a newer one.

Do you have another wifi card or another OS you could try?

---

