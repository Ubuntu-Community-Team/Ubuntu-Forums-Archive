---
title: "Update broke wireless detection"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by rajan on 2010-08-10
Hi all, it seems like there are a lot of people on here that are having the same problem with the 10.04's version of the wireless software. I don't feel that it is Network Manager's fault since I installed WICD side-by-side with it and it too could not detect the router in the room. 

I don't know what to do. I installed the 10.04 OS as a complete reformat, and everything worked spectacularly, however, after an update about a month ago the wireless stopped detecting routers. 

The other components work fine (the ethernet is still working), but the wireless needs to work on a laptop, right?

Here are some of the important details:

Last line of lspci:
```

02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)

```

```

rajan@saraswati:~$ uname -a
Linux saraswati 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux

```

```

rajan@saraswati:~$ sudo lshw -C Network
[sudo] password for rajan: 
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:1b:7d:af
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=128.101.162.245 latency=32 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:11 memory:faffe000-faffffff
  *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:7 memory:faff6000-faff7fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:96:b6:a3:9b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

Any help is appreciated. I really need this wireless before Thursday.


EDIT:

I should also point out that I was able to detect wireless connections when I was using my friend's USB wireless modem, so I think it must be a hardware/driver-specific issue. 

If anyone has any idea of how to get some information on the driver's ability to "drive" the device, or anything else, I'm all ears.

---

### Post by Peter09 on 2010-08-10
The BroadCom drives will become available after your first update (you will need to do it hard wired I guess)
 
Look in System->Administration->Hardware to see if the drivers are waiting for you to enable them.

---

### Post by Oodi on 2010-08-10
My problem is similar to this and in going to the specified location, there is no option to enable the driver, nor does it even appear.

---

### Post by Peter09 on 2010-08-10
Oodi
 
Trouble is that a lot of these problems look similar but need different solutions.
 
Can I suggest you start a new thread, re-state the problem and provide the output if the commands
 
```
ifconfig
```
 
and
 
```
lshw -C network
```
 
Do not have a hard wired connection connected when you do these commands.

---

### Post by Oodi on 2010-08-10
Have already started a new thread, give me a second to post the new information. "[10.04, Broadcom, Can't Enable Wireless Device]("http://ubuntuforums.org/showthread.php?t=1549722")"

---

### Post by rajan on 2010-08-10
> **Peter09 said:**
> The BroadCom drives will become available after your first update (you will need to do it hard wired I guess)
 
Look in System->Administration->Hardware to see if the drivers are waiting for you to enable them.

Peter09, thanks for the reply. I've enabled and removed that driver about 5 times hoping for some resolution. On first install it was working great, but now it seems to have incorporated a bug.

---

### Post by rajan on 2010-08-10
here's the "i'm a total idiot" post. 

upon reading oodi's thread i tried toggling my wireless on-off switch, and a few minutes later, it started working. 

to be fair, i did try to toggle it before, but i guess it takes a while to activate. 

in any case, i'm not too proud to admit a nice, big, dumb mistake.

---

### Post by Peter09 on 2010-08-10
:d

---

### Post by geezer88 on 2010-08-11
Actually, this post was what I needed.  I was having the same problem with an Inspiron 15.  The wireless switch is not that obvious (it's F2, instead of Fn-F2 as posted in some places, and takes a couple of seconds to activate), and the switch appears to be off by default.  Yours was not the first thread I saw where the switch was ultimately the problem, so that convinced me to check it again until I got it right.  Anyway, thanks!

---

