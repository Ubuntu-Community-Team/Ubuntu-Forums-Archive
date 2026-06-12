---
title: "cannot connect wireless bcm4311"
date: 2010-11-12
forum: Networking &amp; Wireless
---

### Post by ashleyleighann on 2010-11-12
Having problems getting wireless connected. Enable wireless is greyed out and not selected. I ran ifconfig iwconfig and rfkill list and these were the results. I don't know what to do, I haven't found anything in any of the forums for this. i have an HP dv5000 i have already tried to turn it on with the switch. when i press the button nothing happens. PLEASE HELP!!! 

ashley@ashley:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:0b:e1:55  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:680 errors:0 dropped:0 overruns:0 frame:0
          TX packets:680 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:54464 (54.4 KB)  TX bytes:54464 (54.4 KB)

ashley@ashley:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

ashley@ashley:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

ashley@ashley:~$ rfkill unblock
Usage:    rfkill [options] command
Options:
    --version    show version (0.4)
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm
ashley@ashley:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

### Post by ashleyleighann on 2010-11-12
Solved!!!

---

### Post by grahammechanical on 2010-11-13
What! solved? How? Please share. Be part of the community. Please. Mark the thread as solved.

Regards.

---

### Post by ashleyleighann on 2010-11-13
I used a usb wireless card to connect to the internet and run updates. installed the b34 wireless driver instead of the STA, STA wouldn't work for me. After that haven't had a problem. Marked the thread as solved :) 

Ash

---

