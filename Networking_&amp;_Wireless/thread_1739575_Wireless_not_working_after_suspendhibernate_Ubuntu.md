---
title: "Wireless not working after suspend/hibernate Ubuntu 10.10 I HAVE TRIED EVERYTHING"
date: 2011-04-26
forum: Networking &amp; Wireless
---

### Post by shooterfinn on 2011-04-26
Hello,

I have just installed Ubuntu 10.10 using wubi, and to be honest, it is not all its cracked up to be. I haven't actually had time to have a good play around with it, because I've been fixing (or at least attempting to fix) many bugs. 

The most annoying problem is this: 

After a suspend or hibernate, my wireless is disabled and will not reactivate. I have read many threads about this same problem with other computers, but every solution I have found has not worked for me. Besides getting incredibly frustrated, I have sort of lost track of what files I have edited through terminal, and now I am worried as I don't know what I have done. Can someone please help me? My laptop is a Compaq Presario a900. If you need any additional info (eg my wireless drivers etc), let me know.

Thank you so much for any support. I am just so fed up.

shooterfinn

---

### Post by lmarmisa on 2011-04-27
I propose a workaround.

Configure your system in such a way that it does not suspend or hibernate.

Configure System -> Preferences -> Screensaver and Power Management too.

---

### Post by eddie3000 on 2011-04-27
I am no expert in Ubuntu (nor linux). At the beginning I used to get all frustrated and upset too when things didn't work. After a couple of years I can say that I am used to getting things that don't work to work, and it is a very instructive thing.
Windows normally just works, but they have loads of employees working on the os and they also charge you for it.
One thing I like about ubuntu (at least in my case) is that it takes less to boot and shut down than windows. I have never needed the suspend or hibernate.
I am sorry to say that I can't help you with your problem. Just want to encourage you to carry on using ubuntu. It won't let you down.

---

### Post by abhilashm86 on 2011-04-27
try this when you login back after suspend. Open up a terminal, 
```
sudo /etc/init.d/networking restart
```
Also try switching off and on your wireless button on your laptop, might be a solution.

---

### Post by dragonfly41 on 2011-04-27
Recently I lost Internet connection .. although I have cable connection and not wireless .. this thread might offer some tips ..

[http://ubuntuforums.org/showthread.php?t=1735427](http://ubuntuforums.org/showthread.php?t=1735427)

see also this current thread ..

[http://ubuntuforums.org/showthread.php?t=1679605](http://ubuntuforums.org/showthread.php?t=1679605)

---

### Post by nothingspecial on 2011-04-27
What is your wireless card

```
sudo lshw -C network
```

Post what ever the terminal tells you back here.

---

### Post by Timmer1240 on 2011-04-27
Ubuntu is going to work better installed in its own partition instead of using wubu just from my experience I know this to be true!

---

### Post by shooterfinn on 2011-04-27
> **nothingspecial said:**
> What is your wireless card

```
sudo lshw -C network
```Post what ever the terminal tells you back here.

Here are the details when I put in that code - 

  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 02
       serial: 00:1c:bf:9a:a0:bb
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.35-28-generic firmware=15.32.2.9 ip=192.168.1.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:42 memory:91300000-91300fff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:f5:7e:66
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:16 ioport:1000(size=256) memory:91200000-912000ff

I really do appreciate you taking the time to help. I would love to get this problem sorted. Thank you :)

---

### Post by Rogeriototh on 2012-05-01
I am actually having the same issue. I am wondering if you've found a solution. 

Just updated to Ubuntu 12.04, imagining that I would have the problem fixed, but it still there. When clicking on the "network manager" icon, I get "Device is not ready" in the Wireless Network section and options are disable. When trying yo enable the wireless card (by pushing the physical Wireless On-Off button) it doesn't do anything.

My Network Card is PRO/Wireless 3945ABG [Golan] Network Connection (Intel)

I appreciate any help.

Thank you,

Rogerio

---

