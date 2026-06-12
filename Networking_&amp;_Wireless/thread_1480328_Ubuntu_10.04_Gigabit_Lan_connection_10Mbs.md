---
title: "Ubuntu 10.04 Gigabit Lan connection 10Mb/s"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by vladimirc on 2010-05-11
Hi there,

I recently did a clean install of Ubuntu 10.04 on my machine. It previously had windows 7 on it and everything worked flawlessly. Now the gigabit LAN connection only connects at 10Mb/s under Ubuntu. I installed a virtual machine with windows 7 and there it connects at 1Gb/s.

I have a linksys WRT610N router which has 4 gigabit ports. I would appreciate if anyone can help me out solving this issue.

Thanks!  

Motherboard: MSI 760GM-E51
CPU: AMD Phenom II X4 955
MEM: 8Gb DDR3
NIC: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

vladimir@aquarius:~$ sudo lshw -C network
[sudo] password for vladimir: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: **:**:**:**:**:**
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.*.* latency=0 link=yes multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:e800(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdff8000-fdffbfff(prefetchable) memory:febe0000-febfffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes


Here's the output of ethtool:


vladimir@aquarius:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: yes

---

### Post by tgalati4 on 2010-05-11
man ethtool

sudo ethtool eth0 speed 1000

sudo ethtool eth0

---

### Post by doas777 on 2010-05-11
make sure your cabling is Cat5E. 
I had this problem a few years ago, when I forgot that i i had jacked my server into my router instead of my switch, to reduce switch uplink traffic for DNS querries. great for DNS, horrible for fileserving.

I spent a full day on that issue, before I got around to checking the cabling. talk about facepalm.

---

### Post by vladimirc on 2010-05-11
The cable is fine because on windows 7 the connection light in the router is green for gigabit and blue in Ubuntu.

for the command:

sudo ethtool eth0 speed 1000

I got the following error: 

ethtool: bad command line argument(s)
For more information run ethtool -h

---

### Post by tgalati4 on 2010-05-11
sudo ethtool -s eth0 speed 1000

---

### Post by vladimirc on 2010-05-11
> **tgalati4 said:**
> sudo ethtool -s eth0 speed 1000

That didn't work. the connection is still at 10 mb/s

---

### Post by tgalati4 on 2010-05-12
Time to file a bug against the network card driver.

Post the output of:

lsmod

---

### Post by 4tro on 2010-05-12
I'm experiencing this very same problem, so i'll post my lsmod


quattro@Defiant:~$ lsmod | grep r816
r8169                  39554  0 
mii                     5237  1 r8169

---

### Post by 4tro on 2010-05-12
> **4tro said:**
> I'm experiencing this very same problem, so i'll post my lsmod


quattro@Defiant:~$ lsmod | grep r816
r8169                  39554  0 
mii                     5237  1 r8169

i solved this issue by installing the driver provided by realtek as suggested by: [http://ubuntuforums.org/showthread.php?t=1022411&highlight=RTL8111%2F8168B](http://ubuntuforums.org/showthread.php?t=1022411&highlight=RTL8111%2F8168B)

i just unpacked and ran sudo autorun.sh which removed the kerneldriver and installed the realtek one

4tro

---

### Post by vladimirc on 2010-05-12
> **tgalati4 said:**
> Time to file a bug against the network card driver.

Post the output of:

lsmod

vladimir@aquarius:~$ lsmod | grep r816
r8169 39554 0
mii 5237 1 r8169

---

### Post by vladimirc on 2010-05-12
> **4tro said:**
> i solved this issue by installing the driver provided by realtek as suggested by: [http://ubuntuforums.org/showthread.php?t=1022411&highlight=RTL8111%2F8168B](http://ubuntuforums.org/showthread.php?t=1022411&highlight=RTL8111%2F8168B)

i just unpacked and ran sudo autorun.sh which removed the kerneldriver and installed the realtek one

4tro

still no luck. the driver r8168 is loaded as you can see below but the connection is still 10Mb/s

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 7596
	Flags: bus master, fast devsel, latency 0, IRQ 28
	I/O ports at e800 [size=256]
	Memory at fdfff000 (64-bit, prefetchable) [size=4K]
	Memory at fdff8000 (64-bit, prefetchable) [size=16K]
	Expansion ROM at febe0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8168
	Kernel modules: r8168

---

### Post by tgalati4 on 2010-05-13
I presume you tried the mii-tool that was shown in the above thread?

Try turning off the computer, unplugging from the wall, and pull the power connector on the motherboard.  Modern ethernet cards use digital tuners and they retain gain settings between reboots.  It's possible that your network card is scrambled and it needs to be reset.

---

### Post by doas777 on 2010-05-13
now just to be sure, you are using a straight-thru cable right? some network card drivers can automatically remap crossover cable pinouts to use it as straight-thru, and that feature may only be available on the windows driver. 
just a thought

---

### Post by vladimirc on 2010-05-13
> **tgalati4 said:**
> I presume you tried the mii-tool that was shown in the above thread?

Try turning off the computer, unplugging from the wall, and pull the power connector on the motherboard.  Modern ethernet cards use digital tuners and they retain gain settings between reboots.  It's possible that your network card is scrambled and it needs to be reset.

Did a cold boot with the network cable unplugged. Then connected later and it worked. Awesome, Thanks a lot, I'm really grateful for the help!

---

### Post by jmaasing on 2010-07-05
> **vladimirc said:**
> Did a cold boot with the network cable unplugged. Then connected later and it worked. Awesome, Thanks a lot, I'm really grateful for the help!

Same problem here, messed about with ethtool and mii-tool but nothing helped. Removed the network cable and the power chord from the computer, waited for 15 minutes and powered up. Now I get 1Gigabit again. Thanks for the tip :)

---

### Post by mrashley on 2010-09-09
It worked for me too! :)

---

### Post by Wlo on 2010-10-21
Just found this thread.  Was having lots of odd problems ( [http://ubuntuforums.org/showthread.php?p=10004787#post10004787](http://ubuntuforums.org/showthread.php?p=10004787#post10004787) ) and the disconnecting the power thing fixed it for me.

Thanks loads :>

---

### Post by Quan-Time on 2010-11-27
Ive been getting the SAME issue, but on a laptop.  I will note that my battery was run flat, and now its doing 10/100 not gbit.  Ill wait till its fully charged, reboot, and go from there.  See which combination works.

---

### Post by Quan-Time on 2010-12-02
bit random.. i cant exactly eliminate WHAT causes non gbit on my laptop.

Asus K7I0C model.. weird.. Most annoying.  Its sorta random far as i can tell.

---

### Post by Bryan55 on 2011-01-02
tgalati4 wrote> Try turning off the computer, unplugging from the wall, and pull the power connector on the motherboard. Modern ethernet cards use digital tuners and they retain gain settings between reboots. It's possible that your network card is scrambled and it needs to be reset.This worked for me after upgrading to 10.10

Thank you thank you thank you, It to me hours and hours to get here.

Bryan

---

### Post by uraritemate on 2011-01-16
> **tgalati4 said:**
> 

Try turning off the computer, unplugging from the wall, and pull the power connector on the motherboard.  Modern Ethernet cards use digital tuners and they retain gain settings between reboots.  It's possible that your network card is scrambled and it needs to be reset.

Thank You tagalati4,
Thanks for the procedure.
Thank you for posting.

Running a dual boot with XP for games and stuff.
Ethernet would drop out booting to Ubuntu 9.10.
Would not recognise Ethernet from cold boot.
10.04 on cd would not connect. and so on.
Windows no problem, of course, must be the new WOW (sic) factor.
ISP did some maintenance on 13/01/1, since then no Ethernet for Ubuntu.

Dual booting for 150 days, modem functioned without hitch for 1 year 10 months.
Rummaging for 3days for a solution.

Ethernet came up on the Dyanlink modem with the computer off.
After following disconnect from NIC socket advice.
And Disconnecting AC power.
Ethernet stays up after shutting down XP

Have a feeling this should be sticky somewhere?

Happy Ubuntu user's again
Have a really good1.
From Australia.
Cheers mate.
uraritemate.

---

### Post by tokyo-joe on 2012-05-27
I am having the exactly same issue, and the total power off method works.

However, it happens so often in my systems. It's very annoying. How can I avoid this issue in the future?

By the way, my machine is configured to boot multiple linux distributions. Does it have something to do with the issue?

---

### Post by oldos2er on 2012-05-27
Closed, please start a new thread since this one is two years old.

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

