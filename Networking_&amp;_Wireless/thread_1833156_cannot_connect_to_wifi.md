---
title: "cannot connect to wifi"
date: 2011-08-25
forum: Networking &amp; Wireless
---

### Post by http:// on 2011-08-25
Hi,

I'm having a problem to connect to the network at home via wifi, open or protected. Using ubuntu 11.04, attached are more details. 
I've managed to get a successful connection on an open network at work. Any idea anyone ?

Thanks for helping

---

### Post by praseodym on 2011-08-25
Hi,

can you additionally show:

```
rfkill list
sudo iwlist scan
dmesg | egrep 'iwl|switch|radio|kill|wmi'
```

---

### Post by http:// on 2011-08-25
Thanks for your quick reply praseodym : ) Attached is the output to the commands you've suggested

---

### Post by praseodym on 2011-08-25
Your router is broadcasting via N-mode? Intel shuts off this mode per default, it can be activated via:

```
echo "options iwlagn 11n_disable=0" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rf iwlagn
sudo modprobe -v iwlagn
sudo service network-manager restart
```
Controls:
```
iwconfig
ifconfig -a
rfkill list
```
Which cell do you want to connect to?

---

### Post by http:// on 2011-08-26
The router uses AP mode and the ESSID i try to connect to is called Channel 3. 
I gave a try to the solution proposed anyhow. It's not making any difference. You can see the output in the attachment

---

### Post by praseodym on 2011-08-26
There is a lot of traffic around "Channel 3" on channel 3, try channel 1 instead, the interferences should decrease, see the picture [here]("http://john.de-graaff.net/wiki/doku.php/links/wlan"). Sometimes "Blanks" in the ESSID cause problems, too.

---

### Post by http:// on 2011-08-26
I tried without whitespace and different channels, it makes no difference unfortunately. Here is some output using Channel 1 as suggested + ESSID="Channel1" with no security set.
   

```
m@hp:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Channel1"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0C:F6:31:FC:A8   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

m@hp:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 68:b5:99:e5:52:46  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6ab5:99ff:fee5:5246/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1566 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1574 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:937244 (937.2 KB)  TX bytes:270518 (270.5 KB)
          Interrupt:20 Memory:d7400000-d7420000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2785 (2.7 KB)  TX bytes:2785 (2.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:d7:4f:b9:14  
          inet6 addr: fe80::224:d7ff:fe4f:b914/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4940 (4.9 KB)  TX bytes:18548 (18.5 KB)

m@hp:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
m@hp:~$ 
```

---

### Post by http:// on 2011-08-26
Got it : ) As you've suggested, it looked like some router configuration incompatible with the default driver settings so i've played around and found that by disabling 'WMM' (no idea what it is) i can get a connection. Both on open and secure. 

Thank you very much for your help praseodym. I wasn't suspecting a configuration incompatibility since there is no issue under windows.

I'll just throw in some keywords for the searches before closing this thread[INDENT] [I]Sitecom WL-153 ([SIZE=2]Rev. A)[/SIZE], Runtime code version       1.45 
 Intel Corporation Centrino Ultimate-N 6300 (rev 35)[/I][/INDENT]

---

