---
title: "Wireless adapter crawling - ideas? new to ubuntu"
date: 2010-02-06
forum: Networking &amp; Wireless
---

### Post by novuntu on 2010-02-06
So I am new to ubuntu and I installed it on both my laptop and my desktop. Laptop worked great and was able to connect to my router. My desktop connects to my router via my wirelesss adapter (Rosewill RNX-N1 [http://www.newegg.com/Product/Product.aspx?Item=N82E16833166025](http://www.newegg.com/Product/Product.aspx?Item=N82E16833166025)) 

but firefox wont even finish loading the first start.ubuntu landing page. In fact it wont finish loading [www.google.com]("http://www.google.com") either. The status bar on the bottom right is like 90% done but never finishes.

Here are the steps I took to trouble shoot:
[B]
1) Ran lsusb[/B]

desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:2870 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[B]
2) Ran iwconfig [/B]

desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"<mysid>"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:0C:XX:D3:XX:96   
          Bit Rate=48 Mb/s   Tx-Power=8 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


3) Ran ifconfig

desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:85:12:97:3b  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:02:6f:68:XX:ba  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2XX:6fff:fe68:XXba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:183 errors:0 dropped:0 overruns:0 frame:0
          TX packets:142 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:68896 (68.8 KB)  TX bytes:18511 (18.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-02-6F-68-XX-BA-36-38-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

4) Went to Network tools and did a ping on [www.yahoo.com]("http://www.yahoo.com")

Got 5 of 5 transmitted and received. 
min: 22.80 ms
average: 265.63 ms
max: 1228.00 ms
packet 3 took the longest 

my laptop is much faster and does not have a N card. 

5) restarted and made sure the adapter was working in windows 7. 

Any thoughts would be much appreciated 

Thanks

---

### Post by chili555 on 2010-02-06
How about letting us see, in a terminal:```
lsmod | grep rt2
```Thanks.

PS - Is this Ralink night? I didn't get the memo!

---

### Post by novuntu on 2010-02-06
> **chili555 said:**
> How about letting us see, in a terminal:```
lsmod | grep rt2
```Thanks.

PS - Is this Ralink night? I didn't get the memo!

desktop:~$ lsmod | grep rt2
rt2870sta             488820  0 
rt2800usb              37372  0 
rt2x00usb              11548  1 rt2800usb
rt2x00lib              29756  2 rt2800usb,rt2x00usb
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
mac80211              181236  2 rt2x00usb,rt2x00lib
cfg80211               93052  2 rt2x00lib,mac80211
crc_ccitt               1852  1 rt2800usb

now I keep getting prompted to re-enter my shared key to connect to my network and it just keeps churning to connect and wont connect.

---

### Post by novuntu on 2010-02-06
> **novuntu said:**
> desktop:~$ lsmod | grep rt2
rt2870sta             488820  0 
rt2800usb              37372  0 
rt2x00usb              11548  1 rt2800usb
rt2x00lib              29756  2 rt2800usb,rt2x00usb
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
mac80211              181236  2 rt2x00usb,rt2x00lib
cfg80211               93052  2 rt2x00lib,mac80211
crc_ccitt               1852  1 rt2800usb

now I keep getting prompted to re-enter my shared key to connect to my network and it just keeps churning to connect and wont connect.

restarting lets me connect to the network but again the browser is just constantly "loading"

---

### Post by chili555 on 2010-02-06
> rt2870sta 488820 0 
rt2800usb 37372 0 These are conflicting modules that are fighting. Please undertake the process here: [http://ubuntuforums.org/showpost.php?p=8786509&postcount=16](http://ubuntuforums.org/showpost.php?p=8786509&postcount=16)

It's evidently also Rosewill night!

---

### Post by novuntu on 2010-02-06
> **chili555 said:**
> These are conflicting modules that are fighting. Please undertake the process here: [http://ubuntuforums.org/showpost.php?p=8786509&postcount=16](http://ubuntuforums.org/showpost.php?p=8786509&postcount=16)

It's evidently also Rosewill night!


looks like it worked! thanks a lot! Really appreciate it! now I just got to figure out how to get my dual monitors working.

---

### Post by novuntu on 2010-02-07
> **chili555 said:**
> These are conflicting modules that are fighting. Please undertake the process here: [http://ubuntuforums.org/showpost.php?p=8786509&postcount=16](http://ubuntuforums.org/showpost.php?p=8786509&postcount=16)

It's evidently also Rosewill night!

One more question. So my browser can access the web but it looks like other things can not. For example when I search for any software via the 'Ubuntu software center" it says 'not available in the current data' and will not let me install it. I double checked and the ubuntu on my laptop does not have this problem. Any thoughts?

---

### Post by chili555 on 2010-02-07
Are the correct software repositories enabled? Please go to System -> Administration -> Synaptic and select Settings -> Repositories and be sure the restricted and multiverse repositories are checked off. Close Repositories and you will be prompted to reload. Press the Reload button and now check to see if your software is available.

---

