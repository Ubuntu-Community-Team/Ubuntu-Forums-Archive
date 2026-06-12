---
title: "Really high ping."
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by gangsterkb on 2011-03-22
Hi Ubuntu Freaks,

I had yesterday a irritating problem that my ping to my router was really high. I had some more little problems and I decided to reinstall the whole thing. 

After I reinstall it and i updated the installation, I check the ping again and that was normal like 0.xxx range. Just like my other PCs running Ubuntu. But now I have that high ping again. 

I have a e3000 Linksys router and the laptop i use has a G adapter. 



From the high ping laptop.
```
jorrit@S1747:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=39.3 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=266 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=64 time=186 ms
64 bytes from 192.168.1.1: icmp_req=4 ttl=64 time=106 ms
64 bytes from 192.168.1.1: icmp_req=5 ttl=64 time=26.0 ms
64 bytes from 192.168.1.1: icmp_req=6 ttl=64 time=253 ms
64 bytes from 192.168.1.1: icmp_req=7 ttl=64 time=173 ms
64 bytes from 192.168.1.1: icmp_req=8 ttl=64 time=93.0 ms
64 bytes from 192.168.1.1: icmp_req=9 ttl=64 time=13.3 ms
64 bytes from 192.168.1.1: icmp_req=10 ttl=64 time=240 ms
64 bytes from 192.168.1.1: icmp_req=11 ttl=64 time=162 ms
64 bytes from 192.168.1.1: icmp_req=12 ttl=64 time=79.9 ms
64 bytes from 192.168.1.1: icmp_req=13 ttl=64 time=307 ms
64 bytes from 192.168.1.1: icmp_req=14 ttl=64 time=228 ms
64 bytes from 192.168.1.1: icmp_req=15 ttl=64 time=148 ms
64 bytes from 192.168.1.1: icmp_req=16 ttl=64 time=68.1 ms
64 bytes from 192.168.1.1: icmp_req=17 ttl=64 time=398 ms
64 bytes from 192.168.1.1: icmp_req=18 ttl=64 time=216 ms
64 bytes from 192.168.1.1: icmp_req=19 ttl=64 time=135 ms
64 bytes from 192.168.1.1: icmp_req=20 ttl=64 time=55.3 ms
^C
--- 192.168.1.1 ping statistics ---
20 packets transmitted, 20 received, 0% packet loss, time 19021ms
rtt min/avg/max/mdev = 13.375/159.889/398.026/100.343 ms

```

From a home server that runs wireless and has also a G adapter.
```
administrator@picard:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=0.586 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=0.573 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=64 time=0.583 ms
64 bytes from 192.168.1.1: icmp_req=4 ttl=64 time=0.828 ms
64 bytes from 192.168.1.1: icmp_req=5 ttl=64 time=0.729 ms
64 bytes from 192.168.1.1: icmp_req=6 ttl=64 time=0.691 ms
64 bytes from 192.168.1.1: icmp_req=7 ttl=64 time=0.590 ms
64 bytes from 192.168.1.1: icmp_req=8 ttl=64 time=0.586 ms
64 bytes from 192.168.1.1: icmp_req=9 ttl=64 time=0.587 ms
64 bytes from 192.168.1.1: icmp_req=10 ttl=64 time=0.587 ms
64 bytes from 192.168.1.1: icmp_req=11 ttl=64 time=4.16 ms
64 bytes from 192.168.1.1: icmp_req=12 ttl=64 time=0.577 ms
64 bytes from 192.168.1.1: icmp_req=13 ttl=64 time=0.484 ms
64 bytes from 192.168.1.1: icmp_req=14 ttl=64 time=0.588 ms
64 bytes from 192.168.1.1: icmp_req=15 ttl=64 time=0.569 ms
64 bytes from 192.168.1.1: icmp_req=16 ttl=64 time=1.16 ms
64 bytes from 192.168.1.1: icmp_req=17 ttl=64 time=0.596 ms
64 bytes from 192.168.1.1: icmp_req=18 ttl=64 time=0.582 ms
64 bytes from 192.168.1.1: icmp_req=19 ttl=64 time=0.578 ms
64 bytes from 192.168.1.1: icmp_req=20 ttl=64 time=1.38 ms
^C
--- 192.168.1.1 ping statistics ---
20 packets transmitted, 20 received, 0% packet loss, time 18997ms
rtt min/avg/max/mdev = 0.484/0.850/4.160/0.789 ms

```

---

### Post by gangsterkb on 2011-03-22
Update: The problem exist only if I run on battery power. Maybe a power management bug?

  Some other system info:
 

```


 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01) 
 Ubuntu 10.10
 2.6.35-22-generic x86_64 


```

---

### Post by NightwishFan on 2011-03-22
Perhaps your device has certain power management features when you go on battery such as increasing the amount of time the device is idle. You can run the following command from the terminal to see if power management is enabled or not:
```
iwconfig
```

Look for a line that says something similar to this:
```
Power Management:off
```

You can try this command to disable power management on the device:
```
sudo iwconfig wlan0 power off
```

This will only work once probably until the device state changes (you plug back in/out or reboot). If this works for the fix to be permanent you may have to set up a script of some kind for when your battery is active. (Which is easy but I do not remember how offhand).  Also note your device may be wlan1 or etc if you have more than one wireless card.

Information about the iwconfig command and it's power management function:
```
       power  Used to manipulate power management scheme parameters and mode.
              To  set  the  period between wake ups, enter period `value'.  To
              set the timeout  before  going  back  to  sleep,  enter  timeout
              `value'.  To set the generic level of power saving, enter saving
              `value'.  You can  also  add  the  min  and  max  modifiers.  By
              default,  those  values are in seconds, append the suffix m or u
              to specify values in milliseconds  or  microseconds.  Sometimes,
              those values are without units (number of beacon periods, dwell,
              percentage or similar).
              off and on disable and reenable power management.  Finally,  you
              may  set the power management mode to all (receive all packets),
              unicast (receive unicast packets  only,  discard  multicast  and
              broadcast)  and multicast (receive multicast and broadcast only,
              discard unicast packets).

              Examples :
                   iwconfig eth0 power period 2
                   iwconfig eth0 power 500m unicast
                   iwconfig eth0 power timeout 300u all
                   iwconfig eth0 power saving 3
                   iwconfig eth0 power off
                   iwconfig eth0 power min period 2 power max period 4


```

---

### Post by gangsterkb on 2011-03-25
That did the trick! Many thanks!

---

### Post by NightwishFan on 2011-03-25
Glad I could help! :)

---

### Post by TheNavigator on 2011-11-04
Same problem here. But:

```

[FONT=monospace]---@Home:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:4  Signal level:194  Noise level:199
          Rx invalid nwid:0  invalid crypt:5  invalid misc:0

---@Home:~$ sudo iwconfig wlan0 power off
[sudo] password for ---: 
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; No such device.

```[/FONT]

---

### Post by xfoe on 2012-11-23
> **TheNavigator said:**
> ```

[FONT=monospace]---@Home:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

[COLOR="red"]eth1[/COLOR]      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:4  Signal level:194  Noise level:199
          Rx invalid nwid:0  invalid crypt:5  invalid misc:0

---@Home:~$ sudo iwconfig [COLOR="Red"]wlan0[/COLOR] power off
[sudo] password for ---: 
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device _wlan0 ; No such device_.

```[/FONT]

Your device seems to be eth1, therefore the command should be

```
sudo iwconfig [COLOR="Red"]eth1[/COLOR] power off
```

---

### Post by wildmanne39 on 2012-11-23
Old thread closed.

---

