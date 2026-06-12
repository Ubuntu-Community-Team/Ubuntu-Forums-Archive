---
title: "Ubuntu 11.04 wired internet slow (disabled ipv6, set MTU)."
date: 2011-06-23
forum: Networking &amp; Wireless
---

### Post by drewg on 2011-06-23
Hello.
My rig:
Gigabyte Z68X GA-UD4-B3 (BIOS latest)
^ Using onboard LAN,
Corsair Vengeance CMZ8GX3M2A1600C8 8GB (2x4GB) DDR3
Intel Core i5 2500K
Gainward 570GTX Stock
Ubuntu 11.04 64bit installed
Running off a Samsung Spinpoint 160GB SATA II HDD (plugged into SATA 2 port)

Router: Billion BiPac 7401VGPR3

I had initial troubles installing Ubuntu, when I'd set a partition to 150GB, it would put down 149,999MB. Which is strange.
Anyway, installation despite the initial troubles was fine. I did this off of the Ubuntu CD. There were no disk errors etc.

My internet is extremely slow when browsing and downloading.
I read about IPv6 maybe slowing it, so I did what was described [here]("http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html").
And added the following lines to /etc/sysctl.conf
```
#disable ipv6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```

I also read numerous posts, one that stood out was (I can't find the link) where a guy said Ubuntu internet was about 25% slower than Windows.
I read it, and looked into my router config, I see the MTU is set to 1492, so I set my wired connection MTU to 1492 via "edit connections" in Ubuntu.

I've also played around and set MTU to below 1492, etc. But it's no help. I get about a maximum speed from my ISP's test files os about 150KB/s where sometimes I can get about 1.5MB/s - nearly 2MB/s. 

So I'm really at a loss, and have no clue as to what to do.
Here's the results of an "ifconfig"
```
eth0      Link encap:Ethernet  HWaddr 1c:6f:65:c6:35:3e  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:20718 errors:0 dropped:20718 overruns:0 frame:20718
          TX packets:15430 errors:0 dropped:119 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26212244 (26.2 MB)  TX bytes:1968305 (1.9 MB)
          Interrupt:41 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:165 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14884 (14.8 KB)  TX bytes:14884 (14.8 KB)


```

I really am at a loss. I recently upgraded my PC, and am looking to getting back into Linux.
All help is appreciated, and thank you in advance.

---

### Post by drewg on 2011-06-24
I'm guessing there's no solution. It's probably the Z68 chipset.

I've tried upgrading the kernel - but no success, the thing just says it was unsuccessful.

---

### Post by drewg on 2011-06-24
Nothing?

---

### Post by varunendra on 2011-06-25
> **drewg said:**
> 
I had initial troubles installing Ubuntu, when I'd set a partition to 150GB, it would put down 149,999MB. Which is strange.
No, this is normal. The partition size is rounded to match cylinder boundaries which most often reduces the actual size than what you defined numerically.

> **drewg said:**
> My internet is extremely slow when browsing and downloading.
I read about IPv6 maybe slowing it, so I did what was described [here]("http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html").
And added the following lines to /etc/sysctl.conf
```
#disable ipv6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```
....
.. looked into my router config, I see the MTU is set to 1492, so I set my wired connection MTU to 1492 via "edit connections" in Ubuntu.

I've also played around and set MTU to below 1492, etc. But it's no help. I get about a maximum speed from my ISP's test files os about 150KB/s where sometimes I can get about 1.5MB/s - nearly 2MB/s.
....
Here's the results of an "ifconfig"
```
eth0      Link encap:Ethernet  HWaddr 1c:6f:65:c6:35:3e  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:20718 errors:0 **dropped:20718** overruns:0 **frame:20718**
          TX packets:15430 errors:0 **dropped:119** overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26212244 (26.2 MB)  TX bytes:1968305 (1.9 MB)
          Interrupt:41 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:165 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14884 (14.8 KB)  TX bytes:14884 (14.8 KB)


```
Apparently you've successfully disabled IPv6 which is a correct step. But still there are packet drops which is not good! Adjusting MTU settings is also a reasonable option, but I think you should've checked physical connectivity first (try replacing cable). An easy way to verify physical connectivity would be to use a different OS on the same machine, like windows or a significantly different linux (slax, puppy, fedora, DSL etc.) to see if the speed improves. But of course it should have the correct driver for your NIC.

> **drewg said:**
> I'm guessing there's no solution. It's probably the Z68 chipset.The Z68 is just a southbridge chip, it has nothing to do with network connection. But the framing error in your ifconfig output does suggest that there may be a driver issue with your network adapter chip. So please post output of following to see which network adapter you have and which driver it is using:
```
sudo lshw -C network
```

I'm no expert on this but hope we can figure it out.

---

### Post by drewg on 2011-06-25
Here's the results:
```
drewg@Drew-PC-Ubuntu:~$ sudo lshw -C network
[sudo] password for drewg:
  *-network              
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 1c:6f:65:c6:35:3e
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.1 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:ee00(size=256) memory:fbcff000-fbcfffff memory:fbcf8000-fbcfbfff
drewg@Drew-PC-Ubuntu:~$

```

---

### Post by varunendra on 2011-06-25
> **drewg said:**
> Here's the results:
```
....
  *-network              
       description: Ethernet interface
       product: **RTL8111/8168B** PCI Express Gigabit Ethernet controller
....
....
....
       configuration: autonegotiation=on broadcast=yes **driver=r8169** driverversion=2.3LK-NAPI duplex=full ip=192.168.1.1 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
....

```
Looks like this very case (broken driver): [http://www.foxhop.net/realtek-dropping-packets-on-linux-ubuntu-and-fedora](http://www.foxhop.net/realtek-dropping-packets-on-linux-ubuntu-and-fedora)
Follow it, then post the above result and result of ifconfig again.

---

### Post by davidaf on 2011-06-25
Same problem here and solved changing Realtek drivers following instructions provided in sugested page ([http://www.foxhop.net/realtek-droppi...ntu-and-fedora](http://www.foxhop.net/realtek-droppi...ntu-and-fedora)).

My hardware:
```
Motherboard: GIGABYTE Z68X-UD3H-B3

root@rivendel:~# lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
```

Sympthoms where the same, slow web surfing that I think was caused by muy crapy internet connection but I was having problems coping files to other lan devices.

Doing ping -f to my network router showed an enormous amount of packet loss.
Searched, found this post, followed instructions and ... PROBLEM SOLVED. 

THANKS :-)

¿Could be a good idea to file a bug in launchpad?

---

### Post by varunendra on 2011-06-25
Glad it helped someone (the suggested page didn't contain any comments, so I was doubtful) :)
> **davidaf said:**
> 
¿Could be a good idea to file a bug in launchpad?
.. Definitely! They should release it with a fixed driver or it being already blacklisted!

---

### Post by drewg on 2011-06-25
Hi,
The fix sort of worked.
However the bit:
```
echo "blacklist r8169" >> /etc/modprobe.d/blacklist.conf
```

Just returns with "access denied".

So I added the blacklist manually, however that didn't seem to help.

Is there any way for me to select which driver to use? The "additional drivers" software has really changed, and I can't seem to enable Ubuntu to use the drivers listed there "realtek, and NVIDIA". So I have no way of actually getting Ubuntu to use a proprietary driver.

Is there some way of making Ubuntu use these drivers?
The manual blacklist didn't work as I said.
So Ubuntu is using the older drivers. And by me installing the newer ones has some how made the (albeit slow) Internet not work at all.

I appreciate the help so far :)

---

### Post by varunendra on 2011-06-25
Driver modules are loaded during kernel loading. So if you have correctly added the module name to blacklist.conf file, then it will be dropped when the system boots. Just reboot and see if the correct driver has been loaded:
```
lshw -C network
```

If the above command still shows the r8169 module in use, verify that the line **blacklist r8169** is correctly added:
```
cat /etc/modprobe.d/blacklist.conf | grep 8169
```

What do you mean 'Additional Driver' software has changed? Is it not in place where it should be or does it not show additional drivers anymore?

---

### Post by drewg on 2011-06-25
> **varunendra said:**
> 
What do you mean 'Additional Driver' software has changed? Is it not in place where it should be or does it not show additional drivers anymore?

For some reason it denied me access when I tried to use the command to add it to blacklist. So I went into CTRL, ALT, F1. Logged in as root, then ran the command.

So all is good now I think.

It's just that I couldn't "choose" the driver listed in additional drivers. It'd say it's active, but not in use. There was no way for me to enable it through that program. Which is odd.

---

### Post by varunendra on 2011-06-25
> **drewg said:**
> ....
....
So Ubuntu is using the older drivers. And by me installing the newer ones has some how made the (albeit slow) Internet not work at all.
..and..
> **drewg said:**
> ....
So all is good now I think.
..seem contradictory to me (I-net not working at all .... all is good??)
What is current situation? I-net working or not?

Which module is in use now (after restart)? (output of)-
```
lshw -C network
```

Generally you have no, or read-only permission for any system file/directory. That's why you need root privilege to edit them. Just check its properties to make sure that 'others' have 'read-only' permission to blacklist.conf file.

As for not being able to choose available 'Additional' drivers, I've no precise idea; just some baseless theories of my own which I don't think are worth discussing here.

---

### Post by drewg on 2011-06-25
Sorry, forgot to do the command (was 1AM lol):


```
drewg@Drew-Desktop-Ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 1c:6f:65:c6:35:3e
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.023.00-NAPI duplex=full ip=192.168.1.1 latency=0 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:41 ioport:ee00(size=256) memory:fbcff000-fbcfffff memory:fbcf8000-fbcfbfff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
drewg@Drew-Desktop-Ubuntu:~$ sudo lshw -C network
[sudo] password for drewg: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 1c:6f:65:c6:35:3e
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.023.00-NAPI duplex=full ip=192.168.1.1 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:41 ioport:ee00(size=256) memory:fbcff000-fbcfffff memory:fbcf8000-fbcfbfff
drewg@Drew-Desktop-Ubuntu:~$ 

```

Looks fine to me, I guess I somehow didn't disable it properly last time. Now it's working fine.

Thanks a lot for the help, I greatly appreciate it.

---

### Post by nm_geo on 2011-06-26
> **drewg said:**
> Hi,
The fix sort of worked.
However the bit:
```
echo "blacklist r8169" >> /etc/modprobe.d/blacklist.conf
```Just returns with "access denied".

So I added the blacklist manually, however that didn't seem to help.


  :)

You need to be root to write to the blacklist.conf file.
Use ```
gksudo gedit /etc/modprobe.d/blacklist.conf
```that will open gedit with root then correct file and save

---

### Post by flusteredpie on 2011-09-24
> **varunendra said:**
> Looks like this very case (broken driver): [http://www.foxhop.net/realtek-dropping-packets-on-linux-ubuntu-and-fedora](http://www.foxhop.net/realtek-dropping-packets-on-linux-ubuntu-and-fedora)
Follow it, then post the above result and result of ifconfig again.

Just wanted to say thanks as this worked for me too (on Linux Mint). Speedtest.net is reporting a speed of 13mbit instead of the 1.2mbit I was getting before. What a difference! :)

---

### Post by varunendra on 2011-09-25
> **flusteredpie said:**
> Just wanted to say thanks as this worked for me too (on Linux Mint). Speedtest.net is reporting a speed of 13mbit instead of the 1.2mbit I was getting before. What a difference! :)
You're welcome! :)

For those who find this thread suffering with the same issue (r8169 driver with RTL8168B adapter), I have posted a 'slightly' modified (a bit simplified) version of the solution here: [http://ubuntuforums.org/showthread.php?p=11053381](http://ubuntuforums.org/showthread.php?p=11053381)

Also on the same page, please follow the post #10 by *rarsa* as he has added some updates which may help those who have kernel 3 series, and this fix doesn't work.

---

### Post by dreamkatana1 on 2011-11-27
That WORKED for me, Thanks everybody.

This should be fixed in Ubuntu right way, COME ON.

---

