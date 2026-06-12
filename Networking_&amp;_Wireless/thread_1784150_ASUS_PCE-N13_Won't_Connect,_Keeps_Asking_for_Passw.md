---
title: "ASUS PCE-N13 Won't Connect, Keeps Asking for Password"
date: 2011-06-16
forum: Networking &amp; Wireless
---

### Post by artoonie on 2011-06-16
Hi all,
I've been debugging for a few days and can't get this to work.

I've tried all of the following suggestions:
[http://ubuntuforums.org/showpost.php?p=9304957&postcount=8](http://ubuntuforums.org/showpost.php?p=9304957&postcount=8)
[http://ubuntuforums.org/showpost.php?p=9933368&postcount=6](http://ubuntuforums.org/showpost.php?p=9933368&postcount=6)
[http://ubuntuforums.org/showpost.php?p=9951781&postcount=3](http://ubuntuforums.org/showpost.php?p=9951781&postcount=3)
With no luck.


Some possibly relevant command line output:
```
$ **sudo ifconfig **
eth1      Link encap:Ethernet  HWaddr bc:ae:c5:68:8b:a2  
          inet addr:10.42.43.99  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::beae:c5ff:fe68:8ba2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4623 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5132946 (5.1 MB)  TX bytes:950197 (950.1 KB)
          Interrupt:47 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

ra0       Link encap:Ethernet  HWaddr 70:71:bc:da:96:70  
          inet6 addr: fe80::7271:bcff:feda:9670/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:53057 (53.0 KB)  TX bytes:1976 (1.9 KB)
          Interrupt:18 

$ **sudo ifconfig wlan0 up**
wlan0: ERROR while getting interface flags: No such device

$** sudo iwconfig **
lo        no wireless extensions.

eth1      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=70/100  Signal level:-68 dBm  Noise level:-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.


```(I'm connected to an ethernet port which connects to my laptop which grabs the wireless, currently.)


Suggestions? Any other output I can provide you with?


Thanks.

---

### Post by DirtyPC on 2011-06-16
I'm confused, are you trying to connect to your wifi via ethernet? Or your actual router settings? (which have a password by default) Or the connection could have a security key.

---

### Post by artoonie on 2011-06-17
> **harrylucas1 said:**
> I'm confused, are you trying to connect to your wifi via ethernet? Or your actual router settings? (which have a password by default) Or the connection could have a security key.
I have a wireless PCE adapter which sees the network and won't connect- it used to be able to for short periods of time, maxing at a few hundred bytes per second, but now it just re-asks for authentication every few minutes without connecting.

This is mostly irrelevant, but:
[COLOR=Gray]My laptop connects to the router just fine, so I daisy-chained the two together so now:

[FONT=Courier New] | router |_  wireless   _| laptop |_  ethernet  _| desktop |[/FONT]
(Bad illustration but hopefully it makes sense.)
So this isn't ideal because I need my laptop on and connected to get desktop internet.

[/COLOR][COLOR=Black]So I'm trying to connect my desktop wirelessly to my router.[/COLOR]

---

### Post by artoonie on 2011-06-18
A shy bump...

---

### Post by artoonie on 2011-06-20
Perhaps this is a more approachable question:
I think the ralink drivers are causing the problems, so how do I get ifconfig to display wlan0 instead of ra0? ie how do i remove the ralink drivers?

---

