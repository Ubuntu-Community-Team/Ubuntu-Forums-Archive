---
title: "Network latency increases over time on a Samsung laptop with Intel wifi (iwlwifi)"
date: 2012-08-19
forum: Networking &amp; Wireless
---

### Post by gkimovski on 2012-08-19
I am running dual boot with Windows 7 and Kubuntu 12.04 on a Samsung Ultrabok with Intel Corporation Centrino Advanced-N 6230 [8086:0091] (rev 34) Wifi. When under Windows, the wifi is behaving normally and I haven't experienced any issues. When running under Kubuntu I am experiencing visible slow down due to increase of the latency over time.

When downloading slows down I can temporarily improve things by running:

```
sudo rmmode iwlwifi
sudo modprobe iwlwifi
```

This are the ping stats before

```
~$ ping google.com
PING google.com (173.194.33.8) 56(84) bytes of data.
64 bytes from sea09s01-in-f8.1e100.net (173.194.33.8): icmp_req=1 ttl=57 time=2047 ms
64 bytes from sea09s01-in-f8.1e100.net (173.194.33.8): icmp_req=2 ttl=57 time=1051 ms
^C
^C64 bytes from 173.194.33.8: icmp_req=3 ttl=57 time=55.9 ms

--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2014ms
rtt min/avg/max/mdev = 55.931/1051.797/2047.466/813.040 ms, pipe 3
```

and after

```
~$ ping google.com
PING google.com (173.194.33.41) 56(84) bytes of data.
64 bytes from sea09s02-in-f9.1e100.net (173.194.33.41): icmp_req=1 ttl=57 time=41.6 ms
64 bytes from sea09s02-in-f9.1e100.net (173.194.33.41): icmp_req=2 ttl=57 time=42.1 ms
64 bytes from sea09s02-in-f9.1e100.net (173.194.33.41): icmp_req=3 ttl=57 time=42.8 ms
^C
--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 41.626/42.190/42.814/0.486 ms
```

I have turned on 11n_disable:

```
$ cat /etc/modprobe.d/51-disable-6235-11n.conf 
options iwlwifi 11n_disable=1
```

I did that earlier since my wifi problems started since I put Kubuntu on the laptop (it was a fresh install as it is a new laptop) and I read that Intel wifi has issues with 11n. That didn't seem to help much, though.

I ran the script from [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) and attached the netinfo file to this thread. The file has the dmesg info after I restarted the iwlwifi module as described above. I will wait and re-run it again once the latency increases and post it here for comparison.

Any advice would be much appreciated!

/Kima

---

### Post by gkimovski on 2012-08-19
I actually solved it myself ;-) It was due to power management problems with the card (or the driver, not sure).

Notice the latency difference in these steps.

I first ran the following while my laptop was on AC power:

```
$ sudo iwconfig wlan0 power off
```

```
~$ ping 192.168.254.254
PING 192.168.254.254 (192.168.254.254) 56(84) bytes of data.
64 bytes from 192.168.254.254: icmp_req=1 ttl=64 time=5.58 ms
64 bytes from 192.168.254.254: icmp_req=2 ttl=64 time=2.17 ms
64 bytes from 192.168.254.254: icmp_req=3 ttl=64 time=1.51 ms
64 bytes from 192.168.254.254: icmp_req=4 ttl=64 time=1.29 ms
64 bytes from 192.168.254.254: icmp_req=5 ttl=64 time=1.61 ms
64 bytes from 192.168.254.254: icmp_req=6 ttl=64 time=1.52 ms
64 bytes from 192.168.254.254: icmp_req=7 ttl=64 time=1.99 ms
64 bytes from 192.168.254.254: icmp_req=8 ttl=64 time=1.38 ms
64 bytes from 192.168.254.254: icmp_req=9 ttl=64 time=2.81 ms
^C
--- 192.168.254.254 ping statistics ---
9 packets transmitted, 9 received, 0% packet loss, time 8012ms
rtt min/avg/max/mdev = 1.299/2.211/5.580/1.273 ms
```

I then ran the following and went on battery power:

```
$ sudo iwconfig wlan0 power on
```

```
~$ ping 192.168.254.254
PING 192.168.254.254 (192.168.254.254) 56(84) bytes of data.
64 bytes from 192.168.254.254: icmp_req=7 ttl=64 time=1702 ms
64 bytes from 192.168.254.254: icmp_req=8 ttl=64 time=695 ms
64 bytes from 192.168.254.254: icmp_req=9 ttl=64 time=1742 ms
64 bytes from 192.168.254.254: icmp_req=10 ttl=64 time=736 ms
64 bytes from 192.168.254.254: icmp_req=11 ttl=64 time=1794 ms
64 bytes from 192.168.254.254: icmp_req=12 ttl=64 time=791 ms
64 bytes from 192.168.254.254: icmp_req=13 ttl=64 time=1829 ms
64 bytes from 192.168.254.254: icmp_req=14 ttl=64 time=826 ms
64 bytes from 192.168.254.254: icmp_req=19 ttl=64 time=1927 ms
64 bytes from 192.168.254.254: icmp_req=20 ttl=64 time=920 ms
^C
--- 192.168.254.254 ping statistics ---
21 packets transmitted, 10 received, 52% packet loss, time 20119ms
rtt min/avg/max/mdev = 695.491/1296.743/1927.622/508.501 ms, pipe 2
```

When keeping the power management off I can go back and forth between AC and battery without issues. I am still not 100% if the latency problems were only due to power management so I will need to monitor but I already had power saving issues related to the display light so I am suspicious that my laptop is not too friendly with 12.04 in general and if I disable all power management it will run much smoother.

/Kima

---

### Post by zsstie on 2013-03-09
thanks very much.
my intel wireless 6235 which work in lubuntu 12.04 have the same issue.
it does make a big difference if you put the ac power plug in.
dont know how to solve it permanently

---

