---
title: "Wired Interface Gone After Suspend"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by btrichardson on 2010-03-21
Hello All,

First I must say I love Ubuntu Netbook Remix. I purchased an Acus 1005HAB Eee PC last week and immediately installed UNR. The redesigned Applications menu is awesome. I've had a few bumps here and there, mainly with the internal mic (wanted to use Skype :). In an attempt to get the internal mic working, I installed some of the linux-backports modules as instructed by some of the forum postings here. It seems as though installing the backports modules may have affected my network interfaces, as they now act funny after resuming from suspend. The wireless comes back, but just says "device not ready" (not worried about wireless right now). However, the wired interface won't come back at all after suspend. I must reboot the machine to get eth0 to be recognized. I read through lots of forum posts about similar issues, but most of them had to do with the wireless interface, not the wired. I saw some posts talking about adding SUSPEND_MODULE instructions to some /etc/pam.d files, but I got the impression those were for NVidia network cards, not the internal cards present in the Eee PCs.

Has anyone else encountered a similar problem with the wired interface? I purged the linux-backports modules I had installed for Alsa (mic and speakers) and rebooted the machine, but still have the same problem so now I don't know if that's what caused it. Both wired and wireless were working flawlessly after resuming from a suspend when I first installed UNR, so I know it's possible! :)

Please help! Having to reboot rather than just suspending, isn't that big of a deal, I would just like to know what I did to mess it up!

--
Thanks!
Bryan

---

### Post by chili555 on 2010-03-21
Please run:```
sudo lshw -C network
```Find out what your ethernet card's driver is. Here is an example:```
*-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       --- snip ---
       configuration: autonegotiation=on broadcast=yes [COLOR="Blue"]driver=e1000e [/COLOR]driverversion=1.0.2-k2 firmware=0.5-1 latency=0 link=no multicast=yes port=twisted pair
```Substitute your details. Then do:```
sudo gedit /etc/pm/config.d/config
```Add a single line:```
SUSPEND_MODULES="your_driver_here"
```If it works, you might try changing it to add your wireless driver, too:```
SUSPEND_MODULES="ethernet_driver wireless_driver"
```Of course, substitute the actual driver name.

Let us know.

---

### Post by btrichardson on 2010-03-21
Hi chili555,

Thank you so much for responding and trying to help me out with this problem. Unfortunately, your suggested solution did not work for me. As you said, I first ran the following:

```

ubuntu:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       --- snip ---
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       --- snip ---
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI duplex=full firmware=N/A ip=10.0.0.29 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s

```

I then added the following to /etc/pm/config.d/config:

```

SUSPEND_MODULES="atl1c ath9k"

```

When that didn't work, I went looking through some previous Ubuntu bug reports on LaunchPad and noticed a few people had suggested doing what you had suggested, except their suggestion was to edit /etc/pm/config.d/local rather than /etc/pm/config.d/config. I renamed the file from config to local, but that didn't seem to do the trick either, even after a restart.

Any other suggestions? Also, any idea why this was working before but not now? I don't think it was do to me installing the linux-backports modules since it's still "misbehaving" after purging them, but maybe so.

--
Thanks again!
Bryan

---

### Post by chili555 on 2010-03-21
Did you try just one module, *atl1c*, for example?

---

### Post by btrichardson on 2010-03-21
Errr... no, I didn't. Sorry for not following your initial instructions. :(

I'll try that and let you know how it went.

--
Thanks!
Bryan

---

### Post by btrichardson on 2010-03-21
Hi Again,

Unfortunately just listing one driver (atl1c) in the file didn't work either. Please note that when editing the file to just list one driver, I also changed the name back to "config" to be consistent the instructions in your first post.

Thanks again for your willingness to help me with this issue. This is why I love Ubuntu (and Linux, and open source software in general)! :)

--
Bryan

---

### Post by btrichardson on 2010-03-23
Just as a follow-up, the suggestion did not work when I renamed the file in /etc/pm/config.d/ from "config" to "local".

Any suggestions?!

--
Thanks!
Bryan

---

### Post by btrichardson on 2010-03-23
I wanted to provide an update on the problem I'm having. I went through the following steps simply to generate more data, hoping someone on the list would know what the problem is after looking at the data generated.

1. Ran "lsmod | grep atl1c"
```

me@ubuntu:~$ lsmod | grep atl1c
atl1c        30880  0

```

2. Ran "lshw -C network"
```

me@ubuntu:~$ lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       --- SNIP ---
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       --- SNIP ---
       configuration: broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A ip=10.0.0.145 latency=0 multicast=yes
       resources: irq:28 memory:f7fc0000-f7ffffff ioport:ec00(size=128)

```

3. Ran "sudo rmmod atl1c"

4. Ran "lsmod | grep atl1c" -> nothing displayed

5. Ran "lshw -C network"
```

me@ubuntu:~$ lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       --- SNIP ---
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbff0000-fbffffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       --- SNIP ---
       configuration: latency=0
       resources: memory:f7fc0000-f7ffffff ioport:ec00(size=128)

```

6. Ran "sudo modprobe atl1c"

7. Ran "lsmod | grep atl1c"
```

me@ubuntu:~$ lsmod | grep atl1c
atl1c        30880  0

```

8. Ran "lshw -C network"
```

me@ubuntu:~$ lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       --- SNIP ---
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       --- SNIP ---
       configuration: broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A ip=10.0.0.145 latency=0 multicast=yes
       resources: irq:28 memory:f7fc0000-f7ffffff ioport:ec00(size=128)

```

So, when the Ethernet module (atl1c) is removed, the hardware list shows the Ethernet interface as "UNCLAIMED", but it still shows the Ethernet interface none-the-less. However, after resuming my laptop after a suspend, running "lshw -C network" only lists my Wireless interface. Running "lsmod | grep atl1c" still lists the module as loaded, and even if I remove and reload the module, running "lshw -C network" still only lists the Wireless interface.

This leads me to think it's not a module problem... its like the laptop is not seeing the Ethernet hardware at all after it resumes. Thoughts?

--
Thanks!
Bryan

---

### Post by btrichardson on 2010-03-28
Hmmm... no takers on this problem huh. Darn, I hoped my previous post would shed some light on the subject. Hopefully this post won't get lost! :)

--
Thanks!
Bryan

---

### Post by in0giro on 2010-08-07
ahoy,

  having the same issue here with Acer Eee PC and Trisquel 3.0 (a Ubuntu derivative) with kernel 2.6.31-22, though 2.6.31-21 seems to work fine.  so it seems to be something in that kernel version, no hardware.  wondering if anyone found a solution, besides a kernel upgrade?

peace/thanks

---

