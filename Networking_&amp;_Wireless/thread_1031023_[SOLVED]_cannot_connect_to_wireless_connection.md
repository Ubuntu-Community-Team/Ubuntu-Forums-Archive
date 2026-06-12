---
title: "[SOLVED] cannot connect to wireless connection"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by laplace/d on 2009-01-04
i just got my new hp pavillion laptop, with an atheros 242x wifi chipset...it doesn´t recognize any wireless network and i havent found any usefull information yet... when  i right click on the connection icon on the tray it doesnt even give the option to connect to a wireless network.... how do i set it up???
if u can help please do so, but remember, i'm a newbie, so fancy solutions are probably going to confuse me.
thanx in advance!

---

### Post by superprash2003 on 2009-01-05
post output of the following from the terminal
1)ifconfig
2)iwconfig
3)lshw -C network
4)iwlist scanning

---

### Post by laplace/d on 2009-01-05
here it is: 

1) 
```
simon@simon-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:8b:4f:32:24  
          inet addr:201.212.214.30  Bcast:201.212.214.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:3164 errors:0 dropped:29240126024 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:191452 (191.4 KB)  TX bytes:4551 (4.5 KB)
          Interrupt:252 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:78 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6016 (6.0 KB)  TX bytes:6016 (6.0 KB)
```

2)

```
simon@simon-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

3)

```
simon@simon-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:4f:32:24
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=201.212.214.30 latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: de:84:ce:3e:45:f0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

4)

```
simon@simon-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

```

---

### Post by superprash2003 on 2009-01-06
try this.. [http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html](http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html)

---

### Post by laplace/d on 2009-01-07
thanx man, now at least the wireless network appears when right clicking, eventhough it is disabled... here's a screenshot of what i get now:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=99059&d=1231346256[/IMG]
(i wasn't online when i took the picture, and the screenshot button doesn't work when the connection tray is right clicked)

anyway, about the link u gave me, i tried solution #1, enabling the wireless card, which was already done...but i did step #1 anyway...nothing changed. when i did step #2, adding those lines to the blacklist, then i got what u see on the screenshot (it said there, that was for PCs which have upgraded from hardy to intrepid, i never upgraded, i did a fresh install of intrepid).

What I would like to know now, is how to get the computer to "see" wireless networks. Say i go to a coffee shop that has wifi, what do i do to go online?

---

### Post by laplace/d on 2009-01-08
hey man thank u very much! forget about the previous post, that was because i wasn't close to any wireless network, as soon as i got close to one the option appeared and it worked like a charm!

---

### Post by upapilot on 2009-01-08
> **laplace/d said:**
> hey man thank u very much! forget about the previous post, that was because i wasn't close to any wireless network, as soon as i got close to one the option appeared and it worked like a charm!
Now that you've got your problem solved please take the trouble of marking the thread as solved and press on the medal icon in the post of the user/s who helped you the most.

---

### Post by laplace/d on 2009-01-08
i'm on it, i didn't know i had to do that, it makes sense, thank u.

---

### Post by ahza on 2009-01-10
To anyone who afraid to try all of above, you can try [**this**]("http://www.webdigity.com/index.php/topic,8202.0.Ubuntu+8.10+-+Atheros+AR242x+problems.html") tutorial, work for me

---

