---
title: "Madwifi and Default Driver?"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by izizzle on 2009-05-11
Ok, Iv'e got a bit of a bug here. Basically, when I use the default driver with my network card (it's a Netgear and uses an Atheros chip), I can browse the internet fine and get full speed when downloading, but when I play online games I lag really bad and get connection interrupts. 

When I use the Madwifi driver with the card, the lag in online games is gone, but my downlaod speeds dwindle down to ~60 kbps from ~160 kbps. Can anyone explan to me what is going on and how to fix it. I have attatched the output of "ifconfig" if that helps at all...BTW: I am using the default driver right now which uses wlan0, but the madwifi driver uses ath0.

```
eth0      Link encap:Ethernet  HWaddr 00:19:21:73:5c:9f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0x6800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:840 (840.0 B)  TX bytes:840 (840.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0f:b5:5d:4b:7b  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fe5d:4b7b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:903 errors:0 dropped:0 overruns:0 frame:0
          TX packets:929 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:876681 (876.6 KB)  TX bytes:187965 (187.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-0F-B5-5D-4B-7B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by pytheas22 on 2009-05-12
Which driver is the 'default driver' and which is the 'Madwifi' one?  There are two families of native Linux drivers for Atheros cards; one is called madwifi and uses a module named 'ath_pci'; the other is usually referred to just as ath9k and uses modules named either ath5k (for older cards) or ath9k (for newer ones).  ath9k/ath5k are basically the 'next-generation' madwifi drivers, and are made by the same developers.

To know which module is driving your card at a particular time, type:
```

lshw -C Network
```

The output will mention which module is driving the device, for example:
```

*-network:0 DISABLED    
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:01:01.0
       logical name: wmaster0
       version: 01
       serial: 00:19:e0:67:8a:f1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: **module=ath5k** broadcast=yes driver=ath5k_pci latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
```

One possible explanation for the behavior you're experiencing is that one of the modules is better than the other at handling UDP packets, which are usually used heavily when playing games, but not for normal Internet browsing.  But in order to know for sure whether this could be the problem and how to fix it, we'd need to figure out which module is associated with which behavior; then we could run some tests to see what's happening to the packets when you're playing games.

It would also be good to know which games you're playing, and which network ports they use.

And just to rule it out: you don't have a firewall set up on Ubuntu, do you?  Unless you set one up manually, this shouldn't be the problem, as Ubuntu comes with all ports enabled by default.

---

### Post by izizzle on 2009-05-12
Hi Pytheas. Here is the output of "lshw -C Network"

```
 *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:05:03.0
       logical name: wmaster0
       version: 01
       serial: 00:0f:b5:5d:4b:7b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.3 latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
```

The "default" driver (which I am currently using) is the ath5k_pci. The games I have tried so far are Savage XR, Urban Terror, and Nexuiz, and all three experience lag with the ath5k_pci driver, but not with the madwifi driver. But, the madwifi lowers my download speed, whereas the ath5k_pci doesn't.

Thanks.

---

### Post by pytheas22 on 2009-05-12
Thanks for the information.  I'm going to need to look a few things up to tell you what to do next, but I'm at work.  If I haven't replied by tomorrow at this time, please remind me.

---

### Post by pytheas22 on 2009-05-14
Please try this: first, load the madwifi driver, then try playing Urban Terror online for a few minutes (it has to be Urban Terror in order to work with the commands below).  Before you start the game, open a terminal and run this command:
```

sudo tcpdump udp port 27952 > ~/Desktop/madwifi.dump
```

Then close the game, and press control-C to kill the process in the terminal.  Next, unload madwifi and replace it with the ath5k module.  Then run this command:

```

sudo tcpdump udp port 27952 > ~/Desktop/ath5k.dump
```

and play Urban Terror again online for a little while.  When you're done, use control-C again to kill the process in the terminal.

When you're done, you'll have two text files on your desktop named madwifi.dump and ath5k.dump.  Please copy the contents of those files here (or if they're really large, upload them as an attachment).  Those files contain information about where the information is going when you're trying to play the game.  If one of the drivers is suffering from a lot of packet loss, this should make that clear.

---

### Post by izizzle on 2009-05-14
I tried it first with the ath5k driver, but it automatically listened on the eth0 device when the wireless is wlan0.

---

### Post by pytheas22 on 2009-05-15
> I tried it first with the ath5k driver, but it automatically listened on the eth0 device when the wireless is wlan0

Sorry, I forgot that you need to specify the interface or it defaults to eth0.  Try listening with this command:
```

sudo tcpdump -i ath0 udp port 27952 > ~/Desktop/madwifi.dump
```

And for ath5k:

```

sudo tcpdump -i wlan0 udp port 27952 > ~/Desktop/madwifi.dump
```

---

### Post by izizzle on 2009-05-15
once again I tried with the ath5k and it recieved 0 packets and sent 0 packets. Weird..but my lag seems to have gone and everything is running rather smoothly. I'll keep you updated though. 

Thanks for all the help!

---

