---
title: "Ubuntu karmic koala 9.10 and Atheros AR5008"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by elect on 2009-11-26
Installation by zero, no wireless found 

```
lspci:

07:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
```


```
elect@elect-laptop:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

```

```
elect@elect-laptop:~$ iwlist wlan0 scan
wlan0     Failed to read scan data : Network is down


```

From what i have read, someone suggests to use madwifi, someone else instead to update athk9, others even to change network manager...

What is the most wise way?

---

### Post by drpjkurian on 2009-11-27
> **elect said:**
> Installation by zero, no wireless found 

```
lspci:

07:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
```


```
elect@elect-laptop:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

```

```
elect@elect-laptop:~$ iwlist wlan0 scan
wlan0     Failed to read scan data : Network is down


```

From what i have read, someone suggests to use madwifi, someone else instead to update athk9, others even to change network manager...

What is the most wise way?

Hi Elect

Please visit my thread and implement it. I am sure it will be solved.
Please visit my thread
[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

With regards
Dr Kurian

---

### Post by elect on 2009-11-27
> **drpjkurian said:**
> Hi Elect

Please visit my thread and implement it. I am sure it will be solved.
Please visit my thread
[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

With regards
Dr Kurian


Ok, with Madwifi driver it works and seems even to be stable with heavy download.

Thanks drpjkurian

---

### Post by drpjkurian on 2009-11-27
> **elect said:**
> Ok, with Madwifi driver it works and seems even to be stable with heavy download.

Thanks drpjkurian

Hi
Thats excellent. I am happy to hear that your problem is solved.

With regards
Dr Kurian

---

### Post by elect on 2009-12-06
> **drpjkurian said:**
> Hi
Thats excellent. I am happy to hear that your problem is solved.

With regards
Dr Kurian



Update the new kernel (.16-generic), it doesnt work more >.>


I can see the wlans, but when i try to connect it takes a lot of time and at the end it doesnt get...

Ideas?

---

### Post by n3had on 2009-12-06
> **elect said:**
> Update the new kernel (.16-generic), it doesnt work more >.>


I can see the wlans, but when i try to connect it takes a lot of time and at the end it doesnt get...

Ideas?

because you've to compile it again at every kernel upgrades

---

### Post by elect on 2009-12-24
> **n3had said:**
> because you've to compile it again at every kernel upgrades

I did, but it continues to not working.

The wireless is really unstable

The network manager gets connection but its impossible to browse, even the ping doesn't work (the same for dhclient, even if it gets the ip). Then it losts connection and reconnect. Looping again and again..

Ideas?

---

### Post by elect on 2009-12-24
elect@elect-laptop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=47.3 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=64 time=4.47 ms
^C
--- 192.168.1.1 ping statistics ---
15 packets transmitted, 2 received, 86% packet loss, time 14045ms
rtt min/avg/max/mdev = 4.470/25.898/47.327/21.429 ms
elect@elect-laptop:~$ ping 208.67.222.222
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.
64 bytes from 208.67.222.222: icmp_seq=4 ttl=54 time=74.4 ms
64 bytes from 208.67.222.222: icmp_seq=17 ttl=54 time=61.5 ms
^C
--- 208.67.222.222 ping statistics ---
18 packets transmitted, 2 received, 88% packet loss, time 17058ms
rtt min/avg/max/mdev = 61.542/67.998/74.455/6.461 ms
elect@elect-laptop:~$


Edit: tried even wicd, it sees no wifi..


Edit2: regarding this 

[http://madwifi-project.org/wiki/Compatibility/Atheros](http://madwifi-project.org/wiki/Compatibility/Atheros)

it should be the Atheros AR5008E-3NX coz its the only one with abgn (as mine, plus bluetooth)

---

### Post by elect on 2009-12-24
It works.

I tried to go on [http://madwifi-project.org/](http://madwifi-project.org/)

And i read "In case you use kernel 2.6.25 or newer, you need to get this snapshot"

So i tried that one. Downloaded and installed. No success, so i put back the blacklist file (that is delete the blackisting of athk5 and athk9).

It works, maeby its not really fast, but it works.


Thanks all, kisses :lolflag:

---

