---
title: "Networking disabled"
date: 2010-06-08
forum: Networking &amp; Wireless
---

### Post by jeffrey2009 on 2010-06-08
Anyone know why sometimes after I reboot my networking is disabled?  i have to right click and enable networking and everything works fine,just a minor annoyance.

---

### Post by w1zard on 2010-06-09
I'm seeing the exact same behaviour on an install of 10.04 too - beginning to wonder if this is a bug?

Just seems to disable itself randomly on startup. Clicking 'Enable networking' fixes it for that session....until next time it happens!

---

### Post by DavorC on 2010-06-09
Have you had a failed hibernate that locked up and you had to do a hard reboot?

Apparently, the problem is that the Network Manager marks network interfaces disabled during the hibernate, and re-enables them on suspend. When hibernate fails and the user has to reboot, the second step never executes, and the interfaces remain disabled, as far as NM is concerned.

See [http://osdir.com/ml/debian-bugs-dist/2010-01/msg07864.html](http://osdir.com/ml/debian-bugs-dist/2010-01/msg07864.html) (or LaunchPad bug #524565) for details and a fix (which worked for me): 
```

 service network-manager stop
 rm /var/lib/NetworkManager/NetworkManager.state
 service network-manager start

```

---

### Post by w1zard on 2010-06-16
Thanks DavorC - that workaround did the trick. Seems it's a known bug in NetworkManager that's already been fixed upstream. Just waiting for the fix to come downstream - associated bug report is here:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/524454](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/524454)

---

### Post by bnhrobotics on 2010-07-07
I tried removing the network manager state, but that did not fix anything.

Below is the output of lshw. 


```
bryan@bryan-desktop:~$ sudo lshw -C network
[sudo] password for bryan: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 00:24:1d:1d:e2:dd
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half ip=192.168.0.100 latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:de00(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdff8000-fdffbfff(prefetchable) memory:fdf00000-fdf1ffff(prefetchable)
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1d:0f:b0:d5:42
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.198 multicast=yes wireless=IEEE 802.11bg
bryan@bryan-desktop:~$ 
```

edit: oops this was mean to go in a different thread

---

### Post by Worsel on 2010-07-12
> **DavorC said:**
> Have you had a failed hibernate that locked up and you had to do a hard reboot?

Apparently, the problem is that the Network Manager marks network interfaces disabled during the hibernate, and re-enables them on suspend. When hibernate fails and the user has to reboot, the second step never executes, and the interfaces remain disabled, as far as NM is concerned.

See [http://osdir.com/ml/debian-bugs-dist/2010-01/msg07864.html](http://osdir.com/ml/debian-bugs-dist/2010-01/msg07864.html) (or LaunchPad bug #524565) for details and a fix (which worked for me): 
```

 service network-manager stop
 rm /var/lib/NetworkManager/NetworkManager.state
 service network-manager start

```

Hi, newbie here. I am having the network disabled problem due to the suspend issue.

I tried pasting the code you provided into the terminal but I'm not having any luck. I'm getting this message each time:

stop: Rejected send message, 1 matched rules; type="method_call", sender=":1.61" (uid=1000 pid=1711 comm="stop) interface="com.ubuntu.Upstart0_6.Job" member="Stop" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

Any help would be much appreciated. :)

---

### Post by dineshs on 2010-07-12
Worsel,
Can you try this
```
gksudo gedit /var/lib/NetworkManager/NetworkManager.state
```
and set```
NetworkingEnabled=true
```

---

### Post by macdo on 2010-07-19
Worsel, 

You need to start each line by sudo:
```
sudo service network-manager stop
 sudo rm /var/lib/NetworkManager/NetworkManager.state
 sudo service network-manager start
```

This will ask you for your password - but then it should work!


Hope that helps, 

macdo

---

### Post by Worsel on 2010-07-19
Thanks guys, managed to sort it out now.:D

---

### Post by edanto on 2010-09-17
Thanks this also helped me too!

---

### Post by crokett on 2010-09-17
This thread helped me too.

A very simple script, just open a new doc, copy and paste, save it and then set the executable permission.

```

#!/bin/bash
#script to restart networking after failed suspend

sudo service network-manager stop
 sudo rm /var/lib/NetworkManager/NetworkManager.state
 sudo service network-manager start

```

---

### Post by edanto on 2010-09-21
hmmm, another restart, and the same networking disabled error.

I can use this code to sort it out, but any suggestions why it might have happened again and what I could do to stop it from happening please?

---

### Post by Old Codger on 2010-09-22
> **crokett said:**
> This thread helped me too.

A very simple script, just open a new doc, copy and paste, save it and then set the executable permission.

```

#!/bin/bash
#script to restart networking after failed suspend

sudo service network-manager stop
 sudo rm /var/lib/NetworkManager/NetworkManager.state
 sudo service network-manager start

```

Many thanks, I was also having the same problem, but the script solved it. :)

---

### Post by drorata on 2010-10-04
Worked for me as well!
Thanks!

---

