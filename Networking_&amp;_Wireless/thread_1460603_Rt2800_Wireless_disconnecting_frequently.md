---
title: "Rt2800 Wireless disconnecting frequently"
date: 2010-04-23
forum: Networking &amp; Wireless
---

### Post by pissedoffdude on 2010-04-23
My wireless card disconnects frequently and sometimes it won't even connect at all.  I've googled the card and the driver and it looks like others are having similar issues as well. [http://bbs.archlinux.org/viewtopic.php?id=94929]("http://bbs.archlinux.org/viewtopic.php?id=94929") [http://ubuntuforums.org/showthread.php?t=1082812]("http://ubuntuforums.org/showthread.php?t=1082812")

My lspci | grep  -i network is as follows ```
02:01.0 Network controller: RaLink RT2800 802.11n PCI

```

Under iwconfig, it's identified as wlan0, and I'm running kernel x86_64 2.6.32.9

---

### Post by gardelix on 2010-05-05
same problem. I am running 10.04 LTS. It worked fine with 9.04 and 9.10.

---

### Post by ibobo on 2010-06-03
I am also running 10.04 LTS,  it can 't  work ,  some people can solve ? :mad: help !!!

---

### Post by ibobo on 2010-06-03
> **ibobo said:**
> I am also running 10.04 LTS, it can 't work , some people can solve ? :mad: help !!!
 
 someone can help me? :mad:

---

### Post by Requia on 2010-06-09
The problem may be specific to AES encryption.  I've changed my encryption type to TKIP and haven't have any issues (16 hours up so far).

I've also seen reference to conflicts between two modules doing the same job.  run:

```
lsmod | grep rt2
```Either rt2800pci should be present, or rt2860sta.  Not both.

Note: I'm a debian user, so the solution for me may not apply to Ubuntu, but I saw this while I was digging and thought I'd offer the solutions I found anyway.

---

### Post by lister171254 on 2010-06-23
Same problem here. After upgrading from 9 to 10.04 (using the same wireless card)the card does not work any more. It finds the network, but then keeps prompting me for the password (I have WPA & WPA2 enabled) without connecting successfully. It has, however, connected once since the upgrade. 

output from various commands follows.

Thanks

llist@MusicPc:~$ lsmod | grep rt2
rt2860sta             542482  0 


llist@MusicPc:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT2860 Wireless  ESSID:"TheAustrians2"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.422 GHz  Access Point: 00:1F:33:23:E7:3C   
          Bit Rate=130 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-51 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


 irq:21 memory:fdef0000-fdefffff



llist@MusicPc:~$ sudo lshw -c network
  *-network
       description: Wireless interface
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: 7
       bus info: pci@0000:03:07.0
       logical name: wlan0
       version: 00
       serial: 00:1f:1f:34:56:d2
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=32 maxlatency=4 mingnt=2 multicast=yes wireless=RT2860 Wireless
       resources: irq:21 memory:fdef0000-fdefffff

---

