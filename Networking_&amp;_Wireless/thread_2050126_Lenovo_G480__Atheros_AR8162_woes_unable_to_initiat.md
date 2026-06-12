---
title: "Lenovo G480 / Atheros AR8162 woes: unable to initiate wired/dsl"
date: 2012-08-30
forum: Networking &amp; Wireless
---

### Post by sanhing on 2012-08-30
It was time to retire the Lenovo G430 that had run happily with 10.04/10.10/11.04. Out with old, in with the new: Lenovo G480. It's loaded with Windows 7. Nuked Windows 7 and installed 11.04 via a cd. Everything hunky dory, except unable to fire up dsl on ubuntu.

I came here two weeks ago, to no avail. Since when I have installed Windows 7, which does give me DSL. But having now installed as dual boot 12.04, I am still unable to go wired/dsl.

I have been all over the forums. And made a beginning thanks to the sticky on Absolute Begiiners Page: "Linux Command Line Learning Resources". But still not found a solution.

Can someone help me, please.

For starters:

ifconfig
jem@ubuntu:~$ ifconfig
  lo        Link encap: Local Loopback   
  inet addr:127.0.0.1  Mask:255.0.0.0
  inet6 addr: ::1/128 Scope:Host
  UP LOOPBACK RUNNING  MTU:16436  Metric:1
  RX packets:24 errors:0 dropped:0 overruns:0 frame:0
  TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
  collisions:0 txqueuelen:0  
 RX bytes:1456 (1.4 KB)  TX bytes:1456 (1.4 KB)
  ----
That's it, that's all.
----

Here's lshw -C network
jem@ubuntu:~$ sudo lshw -C network
  *-network UNCLAIMED      
  description: Ethernet controller
  product: AR8162 Fast Ethernet
  vendor: Atheros Communications Inc.
  physical id: 0
  bus info: pci@0000:03:00.0
  version: 08
  width: 64 bits
  clock: 33MHz
  capabilities: pm pciexpress msi msix bus_master cap_list
  configuration: latency=0
  resources: memory:d3500000-d353ffff ioport:2000(size=128)
  *-network DISABLED
  description: Wireless interface
  product: BCM4313 802.11b/g/n Wireless LAN Controller
  vendor: Broadcom Corporation
  physical id: 0
  bus info: pci@0000:04:00.0
  logical name: wlan0
  version: 01
  serial: 08:ed:b9:98:d6:39
  width: 64 bits
  clock: 33MHz
  capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
  configuration: broadcast=yes driver=brcmsmac driverversion=3.2.0-23-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
  resources: irq:17 memory:d3400000-d3403fff
  jem@ubuntu:~$ 
 ---

Are there any clues there? Is there something else you need to sort out the problem?
 
You see, I am sure this is solvable. But not by me alone. I am hoping someone out there may help! I have really grown to love ubuntu. I really don't want to have to continue dual booting and choosing Windowz. Cheers!

---

### Post by chili555 on 2012-08-30
First, we need to associate a driver with your ethernet card; it currently has none:> *-network [COLOR="Red"]UNCLAIMED[/COLOR]
description: Ethernet controller
product: AR8162 Fast Ethernet
vendor: Atheros Communications Inc.In order to figure out what driver we need, we need more information. Please run and post:```
lspci -nn | grep 0200
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by sanhing on 2012-08-30
> **chili555 said:**
> First, we need to associate a driver with your ethernet card; it currently has none:In order to figure out what driver we need, we need more information. Please run and post:```
lspci -nn | grep 0200
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

Hi, chili555.
Here:
                                  jem@ubuntu:~$ lspci -nn | grep 0200
  03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 08)
  jem@ubuntu:~$

---

### Post by chili555 on 2012-08-30
> Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] Your device works with the elusive driver *alx*. My long delay in responding was because I was working out how and where to get it working. It will require big downloads and we'll need to get your wireless working first. Do you have an available wireless network you can connect to?> *-network [COLOR="Red"]DISABLED[/COLOR]
description: Wireless interface
product: BCM4313 802.11b/g/n Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:04:00.0
logical name: wlan0
<snip>
configuration: broadcast=yes [COLOR="Red"]driver=brcmsmac[/COLOR] driverversion=3.2.0-23-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
resources: irq:17 memory:d3400000-d3403fffYou have the driver in place and I assume the wireless is disabled because the switch is set to OFF. Confirm:```
rfkill list all
```Flip it to ON and get an internet connection. Then open a terminal and do:```
sudo apt-get install linux-headers-generic build-essential
wget http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.1-1-snpc.tar.bz2
tar -xf compat-wireless-3.5.1-1-snpc.tar.bz2
cd compat-wireless-3.5.1-1-snpc
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx
```Your wired ethernet should now be working.

---

### Post by sanhing on 2012-08-30
[QUOTE=chili555;12206393]Your device works with the elusive driver *alx*. My long delay in responding was because I was working out how and where to get it working. It will require big downloads and we'll need to get your wireless working first. Do you have an available wireless network you can connect to?

Chili555,

Wireless not available here; that's why I need wired/dsl.

FYI, in BIOS I can enable/disable 'wireless', but no such option available for ethernet or suchlike.

It's past midnight here on a little island in the South China Sea. I am logging out. Will check in on Friday as today on my old laptop..  In the meantime, many thanks for your assistance.

---

### Post by chili555 on 2012-08-30
> Wireless not available here; that's why I need wired/dsl.That's too bad. Installing the driver alx will be challenging without it. If you can download the packages to your Windows partition and then transfer them on a USB key, CD or similar, then we can get the job done. First, let's get build-essential: [http://packages.ubuntu.com/precise/build-essential](http://packages.ubuntu.com/precise/build-essential) 

Download the package as appropriate to your architecture; either i386 (32-bit) or amd64 (64-bit). Find out which you have with this command:```
arch
```32-bit will report as i686 and 64-bit as x86_64.

The red dots indicate that the package build-essential depends on dpkg-dev, g++, gcc, libc6-dev or libc-dev and make. Download those packages also.

Now for linux-headers: [http://packages.ubuntu.com/search?keywords=linux-headers-generic&searchon=names&suite=precise&section=all](http://packages.ubuntu.com/search?keywords=linux-headers-generic&searchon=names&suite=precise&section=all)  As you can see, you can download linux-headers-generic or linux-headers-generic-pae. Find out which you need with:```
uname -r
```This package depends on the headers matching your running kernel. That means that, in addition to the 'generic' or generic-pae' package, you'll also need linux-headers for your kernel. For example, if the uname -r command shows that you are running *3.2.0-23-generic*, you will need linux-headers-*3.2.0-23-generic. *

Once you have all these on a USB key or CD, drag and drop these on to the desktop of your Ubuntu installation. Open a terminal and do:```
cd Desktop
sudo dpkg -i *.deb
```The wildcard * means to install every .deb package on your desktop. We hope there are no missing dependencies, but if so, go here, download and install them, too: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Now for compat-wireless. Download this package and transfer it to your Ubuntu desktop. [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.1-1-snpc.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.1-1-snpc.tar.bz2)

Then install it:```
cd Desktop
tar -xf compat-wireless-3.5.1-1-snpc.tar.bz2
cd compat-wireless-3.5.1-1-snpc
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx
```Post back any errors or problems; I'll be glad to help.

We are many timezones apart, so I will look for your post early tomorrow morning.

---

### Post by sanhing on 2012-08-31
> **chili555 said:**
> That's too bad. Installing the driver alx will be challenging without it. If you can download the packages to your Windows partition and then transfer them on a USB key, CD or similar, then we can get the job done. First, let's get build-essential: [http://packages.ubuntu.com/precise/build-essential](http://packages.ubuntu.com/precise/build-essential) 

Download the package as appropriate to your architecture; either i386 (32-bit) or amd64 (64-bit). Find out which you have with this command:```
arch
```32-bit will report as i686 and 64-bit as x86_64.

The red dots indicate that the package build-essential depends on dpkg-dev, g++, gcc, libc6-dev or libc-dev and make. Download those packages also.

Now for linux-headers: [http://packages.ubuntu.com/search?keywords=linux-headers-generic&searchon=names&suite=precise&section=all](http://packages.ubuntu.com/search?keywords=linux-headers-generic&searchon=names&suite=precise&section=all)  As you can see, you can download linux-headers-generic or linux-headers-generic-pae. Find out which you need with:```
uname -r
```This package depends on the headers matching your running kernel. That means that, in addition to the 'generic' or generic-pae' package, you'll also need linux-headers for your kernel. For example, if the uname -r command shows that you are running *3.2.0-23-generic*, you will need linux-headers-*3.2.0-23-generic. *

Once you have all these on a USB key or CD, drag and drop these on to the desktop of your Ubuntu installation. Open a terminal and do:```
cd Desktop
sudo dpkg -i *.deb
```The wildcard * means to install every .deb package on your desktop. We hope there are no missing dependencies, but if so, go here, download and install them, too: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Now for compat-wireless. Download this package and transfer it to your Ubuntu desktop. [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.1-1-snpc.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.1-1-snpc.tar.bz2)

Then install it:```
cd Desktop
tar -xf compat-wireless-3.5.1-1-snpc.tar.bz2
cd compat-wireless-3.5.1-1-snpc
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx
```Post back any errors or problems; I'll be glad to help.

We are many timezones apart, so I will look for your post early tomorrow morning.

Chili555, many thanks for all you have done. I have followed your (easy-to-follow) instructions and now downloaded all the stuff. 
However, some years ago I vowed I would never again do any major installations at night. After a long day, tiredeness can lead ot snafusI So, if you don't mind, I will wait until daylight on Saturday to install. And let you know the result soon after. Again, many thanks for all your help.

---

### Post by chili555 on 2012-08-31
> So, if you don't mind, I will wait until daylight on Saturday to install. No problem at all. I will look forward to your success!

---

### Post by sanhing on 2012-09-01
Chili555 (and everyone else), I am delighted to report that thanks to your know-how and easy-to-follow instructions I am now connected via wired/dsl to the interwebs. Life looked bleak and now it's bright again. Many, many thanks!

---

### Post by chili555 on 2012-09-01
Woo hoo! That is awesome news! Great job.

As with any driver or module that's compiled from source code, it was compiled against your running kernel version only. When you get updates and get a newer kernel version, also known as linux-image, you will need to recompile:```
cd Desktop/compat-wireless-3.5.1-1-snpc
make clean
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx
```You might copy these instructions to your desktop so you'll recall when the time comes.

The *alx* driver is a new arrival and you've worked out a successful install. So the searchers can find the fix, please use thread tools at the top and mark Solved.

---

### Post by sanhing on 2012-09-01
> **chili555 said:**
> Woo hoo! That is awesome news! Great job.

As with any driver or module that's compiled from source code, it was compiled against your running kernel version only. When you get updates and get a newer kernel version, also known as linux-image, you will need to recompile:```
cd Desktop/compat-wireless-3.5.1-1-snpc
make clean
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx
```You might copy these instructions to your desktop so you'll recall when the time comes.

The *alx* driver is a new arrival and you've worked out a successful install. So the searchers can find the fix, please use thread tools at the top and mark Solved.

I make note of your remarks concerning a newer kernel. Again,  many thanks!

---

### Post by Mythek on 2012-09-11
Dear god, finally its been days since i could find this!!!!!!!!!!!!!!!1

---

### Post by roni21 on 2012-09-11
hello, i have a lenovo y580, which has a similar atheros ar8162. i followed the procedure written here. but still no luck. in the network menu i am not getting anything. no wifi and no lan connection. FYI i am connected to a wifi router.

---

### Post by chili555 on 2012-09-11
> similar atheros ar8162Similar?? Let's have a look:```
lspci -nn | grep 0200
sudo modprobe alx
dmesg | grep alx
```> no wifi This is an ethernet device, not wifi.

---

### Post by roni21 on 2012-09-11
well, it worked now. i am from ubuntu now :)
i got some error msg with the driver file you posted. 

> roni@roni-Lenovo-Y580:~/compat-wireless-2012-09-05$ make
./scripts/gen-compat-autoconf.sh /home/roni/compat-wireless-2012-09-05/.config /home/roni/compat-wireless-2012-09-05/config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/3.2.0-29-generic-pae/build M=/home/roni/compat-wireless-2012-09-05 modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
  CC [M]  /home/roni/compat-wireless-2012-09-05/compat/main.o
  CC [M]  /home/roni/compat-wireless-2012-09-05/compat/compat-3.3.o
  CC [M]  /home/roni/compat-wireless-2012-09-05/compat/compat-3.4.o
  CC [M]  /home/roni/compat-wireless-2012-09-05/compat/compat-3.7.o
/home/roni/compat-wireless-2012-09-05/compat/compat-3.7.c: In function &#8216;pcie_flags_reg&#8217;:
/home/roni/compat-wireless-2012-09-05/compat/compat-3.7.c:37:2: warning: passing argument 1 of &#8216;pci_find_capability&#8217; discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]
include/linux/pci.h:713:5: note: expected &#8216;struct pci_dev *&#8217; but argument is of type &#8216;const struct pci_dev *&#8217;
/home/roni/compat-wireless-2012-09-05/compat/compat-3.7.c:41:2: warning: passing argument 1 of &#8216;pci_read_config_word&#8217; discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]
include/linux/pci.h:756:19: note: expected &#8216;struct pci_dev *&#8217; but argument is of type &#8216;const struct pci_dev *&#8217;
  CC [M]  /home/roni/compat-wireless-2012-09-05/compat/compat_atomic.o
  CC [M]  /home/roni/compat-wireless-2012-09-05/compat/sch_fq_codel_core.o
  CC [M]  /home/roni/compat-wireless-2012-09-05/compat/flow_dissector.o
  LD [M]  /home/roni/compat-wireless-2012-09-05/compat/compat.o
  CC [M]  /home/roni/compat-wireless-2012-09-05/compat/sch_codel.o
  LD [M]  /home/roni/compat-wireless-2012-09-05/compat/sch_fq_codel.o
scripts/Makefile.build:44: /home/roni/compat-wireless-2012-09-05/drivers/net/ethernet/atheros/alx/Makefile: No such file or directory
make[4]: *** No rule to make target `/home/roni/compat-wireless-2012-09-05/drivers/net/ethernet/atheros/alx/Makefile'.  Stop.
make[3]: *** [/home/roni/compat-wireless-2012-09-05/drivers/net/ethernet/atheros/alx] Error 2
make[2]: *** [/home/roni/compat-wireless-2012-09-05/drivers/net/ethernet/atheros] Error 2
make[1]: *** [_module_/home/roni/compat-wireless-2012-09-05] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
make: *** [modules] Error 2


then i found this [http://askubuntu.com/questions/157223/12-04-does-not-detect-eth0atheros-ar8162](http://askubuntu.com/questions/157223/12-04-does-not-detect-eth0atheros-ar8162) and downloaded compat-wireless-2012-09-01-pc.tar.bz2 file...then it worked. may be you can tell about my problem, so that it might help others. but this is really frustrating when you cant access internet due to driver issue. i am lucky that i have another machine beside.

---

### Post by chili555 on 2012-09-11
> roni@roni-Lenovo-Y580:~/[COLOR="Red"]compat-wireless-2012-09-05[/COLOR]Hmmm. There was a reason that I did:> My long delay in responding was because I was working out how and where to get it working.And therefor there was a reason I did:> compat-wireless-[COLOR="Red"]3.5.1-1-snpc[/COLOR]...because it works.

---

### Post by roni21 on 2012-09-11
hmm...now i have another problem...my wifi is not working :( i just restarted to windows. but if you are online then i can go back :) i spent almost an hour for ethernet driver :(

---

### Post by chili555 on 2012-09-11
> **roni21 said:**
> hmm...now i have another problem...my wifi is not working :( i just restarted to windows. but if you are online then i can go back :) i spent almost an hour for ethernet driver :(If you want to get your wireless going, I suggest you start a new thread. This thread refers to Atheros ethernet and the driver *alx*.

---

### Post by ymblrin on 2012-09-19
Chili555, thank you very much for the steps to enable ethernet on ubuntu.

I had to do the below before "sudo make install" in addition:
"
sudo mv /usr/sbin/update-grub ~/ug.bk; sudo touch /usr/sin/update-grub; sudo chmod a+x /usr/sbin/update-grub;
"
in order to bypass grub update. My live kubuntu 12 uses syslinux boot manager and not grub.

I do not know the long-term consequences of moving update-grub yet.

---

### Post by trajektorijus on 2012-09-26
Hi there,

i followed all the step and eth0 appeared, but i still can't connect to the internet via ethernet...

```

lspci -nn | grep 0200
sudo modprobe alx
dmesg | grep alx

```
Results: 
```
trajektorijus@trajektorijus-Lenovo-IdeaPad-Y580:~$ lspci -nn | grep 0200
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091] (rev 08)
trajektorijus@trajektorijus-Lenovo-IdeaPad-Y580:~$ sudo modprobe alx
trajektorijus@trajektorijus-Lenovo-IdeaPad-Y580:~$ dmesg | grep alx
[   26.025103] alx 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.025105] alx 0000:02:00.0: DMA to 64-BIT addresses
[   26.025119] alx 0000:02:00.0: setting latency timer to 64
[   26.025180] alx 0000:02:00.0: (unregistered net_device): HW Flags = 0x415
[   26.025590] alx 0000:02:00.0: (unregistered net_device): reset PHY, pws = 1, az = 0, ptp = 0
[   26.026947] alx 0000:02:00.0: (unregistered net_device): speed = 0x2f, autoneg = 1
[   26.027975] alx 0000:02:00.0: irq 46 for MSI/MSI-X
[   26.028234] alx: Atheros Gigabit Network Connection
[  292.458570] alx 0000:02:00.0: eth0: speed = 0x2f, autoneg = 1
[  974.582372] alx 0000:02:00.0: eth0: speed = 0x2f, autoneg = 1
[ 1817.587433] alx 0000:02:00.0: eth0: speed = 0x2f, autoneg = 1
trajektorijus@trajektorijus-Lenovo-IdeaPad-Y580:~$ 

```

ifconfig:


```
trajektorijus@trajektorijus-Lenovo-IdeaPad-Y580:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr dc:0e:a1:f0:60:7f  
          inet addr:10.10.11.85  Bcast:10.10.11.255  Mask:255.255.255.0
          inet6 addr: fe80::de0e:a1ff:fef0:607f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:214 errors:0 dropped:7 overruns:0 frame:0
          TX packets:1868 errors:0 dropped:0 overruns:0 carrier:7
          collisions:0 txqueuelen:1000 
          RX bytes:28119 (28.1 KB)  TX bytes:157867 (157.8 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:304397 (304.3 KB)  TX bytes:304397 (304.3 KB)

wlan0     Link encap:Ethernet  HWaddr 9c:4e:36:18:5e:4c  
          inet addr:88.118.228.186  Bcast:88.118.229.255  Mask:255.255.254.0
          inet6 addr: fe80::9e4e:36ff:fe18:5e4c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51960 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31935 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:52478089 (52.4 MB)  TX bytes:4210118 (4.2 MB)

```

lshw -C network:
```
trajektorijus@trajektorijus-Lenovo-IdeaPad-Y580:~$ sudo lshw -C network  *-network               
       description: Ethernet interface
       product: AR8161 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 08
       serial: dc:0e:a1:f0:60:7f
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full firmware=alx ip=10.10.11.85 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:46 memory:d3600000-d363ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 2200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: c4
       serial: 9c:4e:36:18:5e:4c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-31-generic firmware=18.168.6.1 ip=88.118.228.186 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:44 memory:d3500000-d3501fff

```

What i did wrong? Wireless works fine.

---

### Post by chili555 on 2012-09-26
> eth0      Link encap:Ethernet  HWaddr dc:0e:a1:f0:60:7f  
          [COLOR="Red"]inet addr:10.10.11.85[/COLOR]  Bcast:10.10.11.255  Mask:255.255.255.0
          inet6 addr: fe80::de0e:a1ff:fef0:607f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:214 errors:0 dropped:7 overruns:0 frame:0
          TX packets:1868 errors:0 dropped:0 overruns:0 carrier:7
          collisions:0 txqueuelen:1000 
          [COLOR="Red"]RX bytes:28119 (28.1 KB)  TX bytes:157867 (157.8 KB)[/COLOR]
          Interrupt:16 Well, you are connected to *something*! What or where is the ethernet cable plugged in to?? I am puzzled by the 10.10.xx address when the wireless has a 88.118.xx address. I wonder if your router or access point is mis-configured.

---

### Post by trajektorijus on 2012-09-27
> **chili555 said:**
> Well, you are connected to *something*! What or where is the ethernet cable plugged in to?? I am puzzled by the 10.10.xx address when the wireless has a 88.118.xx address. I wonder if your router or access point is mis-configured.

Today i tried to connect at my home. And everything works like a charm. So i guess at my office there was something wrong with configuration... I'll try harder :)

Anyway, thanks for response!

P.S. Wifi had different ip because it was at different place.

---

### Post by Kyora on 2012-10-08
I still can't see eth0 my computer is dell inspiron 5423 14z with Atheros8162 I tried to follow ur advise but didn't work and i also tried h[ttp://askubuntu.com/questions/157223/12-04-does-not-detect-eth0atheros-ar8162]("http://askubuntu.com/questions/157223/12-04-does-not-detect-eth0atheros-ar8162") too but problem is i can't comply the alx do u know y?

---

### Post by chili555 on 2012-10-08
> **Kyora said:**
> I still can't see eth0 my computer is dell inspiron 5423 14z with Atheros8162 I tried to follow ur advise but didn't work and i also tried h[ttp://askubuntu.com/questions/157223/12-04-does-not-detect-eth0atheros-ar8162]("http://askubuntu.com/questions/157223/12-04-does-not-detect-eth0atheros-ar8162") too but problem is i can't comply the alx do u know y?whch advise did u folow? post nr4? were there errs to report?

---

### Post by Kyora on 2012-10-09
I tried to follow this command 

tar -xvf compat-wireless-2012-02-28-p.tar 
cd compat-wireless-2012-02-28-p 
scripts/driver-select alx 
make
 make install
 modprobe alx

while using compat-wireless-2012-09-01-pc.tar.bz2 instead but it have error 
when i try to use "modprobe alx" it like they don't have alx command anymore like in the post said
so i don't know what to do next

---

### Post by Kyora on 2012-10-09
for now i try to follow ur advise  step be step now i'm able to see wire network but i still can't connect them successfully they keep connecting but may be it due to i run command

 $ sudo modprobe alx

and nothing happen

---

### Post by Kyora on 2012-10-09
I try to connect to Ethernet switch but it keep trying to connect with no  success but the Ethernet port work fine w/ router to connect internet do u  got an idea?

---

### Post by chili555 on 2012-10-09
> **Kyora said:**
>  i run command

 $ sudo modprobe alx

and nothing happenWhen you run a command and nothing happens, it means that the command was executed as requested and there are no errors or warnings to report.

Are you using Network Manager to connect? Are there any settings in there you've added? Usually, NM will handle all details for you without any extra settings.

---

### Post by Kyora on 2012-10-12
sry for alte reply i try ur advice step by step and ethernet port are now appear but the problem is when i connect it to ethernet switch it keep connecting and not can't connect while my friend computer can access do u got an idea ??

---

### Post by chili555 on 2012-10-12
> **Kyora said:**
> sry for alte reply i try ur advice step by step and ethernet port are now appear but the problem is when i connect it to ethernet switch it keep connecting and not can't connect while my friend computer can access do u got an idea ??Please run and post:```
nm-tool
```Let's see what's going on behind the scenes.

---

### Post by dhessels on 2012-10-23
I had the same problem with having no wireless, so chili555's instructions in post #5 were perfect! Doubly helpful as a beginner as I learned a lot.

For reference my controller was AR8161 on a P8H77-V ASUS motherboard, using ubuntu 12.10.

Thanks muchly ;)

---

### Post by chili555 on 2012-10-23
> **dhessels said:**
> I had the same problem with having no wireless, so chili555's instructions in post #5 were perfect! Doubly helpful as a beginner as I learned a lot.

For reference my controller was AR8161 on a P8H77-V ASUS motherboard, using ubuntu 12.10.

Thanks muchly ;)Awesome! Glad to hear it. Please read on down to post #10 and retain the instructions and files.

---

### Post by Kyora on 2012-10-24
NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        24:B6:FD:56:77:E4

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [salapaomoosub] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        E0:06:E6:25:8D:D9

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    cronus1:         Infra, 10:6F:3F:13:63:E4, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA
    BUFFALO-1363E0-1:Infra, 10:6F:3F:13:63:E0, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    @TRUEWIFI:       Infra, 00:02:6F:C7:0B:E4, Freq 2462 MHz, Rate 54 Mb/s, Strength 34
    @TRUEWIFI:       Infra, 00:02:6F:B7:6F:50, Freq 2412 MHz, Rate 54 Mb/s, Strength 27
    @ 3BB_WiFi:      Infra, 1C:AF:F7:50:A5:54, Freq 2412 MHz, Rate 54 Mb/s, Strength 20
    @ 3BB_WiFi:      Infra, 1C:AF:F7:50:A2:40, Freq 2462 MHz, Rate 54 Mb/s, Strength 20
    @TRUEWIFI:       Infra, 00:02:6F:B7:5D:3C, Freq 2412 MHz, Rate 54 Mb/s, Strength 14
    gunhotspot13:    Infra, 00:22:6B:73:66:0B, Freq 2462 MHz, Rate 54 Mb/s, Strength 14
    RMPT:            Infra, 00:1F:A4:B5:A2:25, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WEP
    *salapaomoosub:  Infra, 38:60:77:58:31:1F, Freq 2437 MHz, Rate 54 Mb/s, Strength 49 WPA2
    Pbnquin:         Infra, 38:60:77:E7:E1:86, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WEP

  IPv4 Settings:
    Address:         192.168.1.53
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             203.144.206.29
    DNS:             203.144.206.49

---

### Post by MarceloH on 2012-10-24
Hi

I have a very similar problem (using 12.04). My wireless does work, yet my ethernet doesnt.

ifconfig gives
> lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:331 errors:0 dropped:0 overruns:0 frame:0
          TX packets:331 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:45661 (45.6 KB)  TX bytes:45661 (45.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:64:42:e9:80  
          inet addr:132.207.220.155  Bcast:132.207.223.255  Mask:255.255.252.0
          inet6 addr: fe80::21e:64ff:fe42:e980/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1476  Metric:1
          RX packets:5832 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2109100 (2.1 MB)  TX bytes:161005 (161.0 KB)"lshw -C network" gives:
>   *-network               
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:1e:64:42:e9:80
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-32-generic-pae firmware=39.31.5.1 build 35138 ip=132.207.220.155 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:47 memory:feafe000-feafffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:febc0000-febfffff ioport:ec00(size=128)And, "nm-tool" gives:
> NetworkManager Tool

State: connected (global)

- Device: wlan0  [Poly-Public] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        00:1E:64:42:E9:80

  Capabilities:
    Speed:           36 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    eduroam:         Infra, 00:12:7F:99:83:99, Freq 2437 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2 Enterprise
    Poly-Securise:   Infra, 00:12:7F:99:83:91, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2 Enterprise
    eduroam:         Infra, 3C:CE:73:08:F6:E9, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2 Enterprise
    Poly-Securise:   Infra, 3C:CE:73:08:F6:E1, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2 Enterprise
    Poly-Public:     Infra, 3C:CE:73:08:F6:E3, Freq 2412 MHz, Rate 54 Mb/s, Strength 54
    *Poly-Public:    Infra, 00:12:7F:99:83:93, Freq 2437 MHz, Rate 54 Mb/s, Strength 53

  IPv4 Settings:
    Address:         132.207.220.155
    Prefix:          22 (255.255.252.0)
    Gateway:         132.207.220.1

    DNS:             132.207.144.2
    DNS:             132.207.144.3

and finally, "lspci -nn | grep 0200"

> 04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8131 Gigabit Ethernet [1969:1063] (rev c0)


I struggle with this problem for hours  :(

Any help would be greatly appreciated.
Sincerely,

Marcelo

---

### Post by chili555 on 2012-10-25
> **MarceloH said:**
> Hi

I have a very similar problem (using 12.04). My wireless does work, yet my ethernet doesnt.

I struggle with this problem for hours  :(

Any help would be greatly appreciated.
Sincerely,

MarceloYour device is supposed to work with the driver atl1c. Let's load it and see what happens:```
sudo modprobe atl1c
dmesg | grep atl1c
ifconfig
```

---

### Post by Kyora on 2012-10-27
do u got any idea about mine problem??

---

### Post by chili555 on 2012-10-27
> **Kyora said:**
> do u got any idea about mine problem??Please plug in the ethernet, try to connect and run and post:```
sudo cat /var/log/syslog | grep -e etwork -e alx | tail-n20
```Sorry for the delay in replying.

---

### Post by KFwLsKvVAs on 2012-11-12
Chili555,

I've been using your instructions for getting the alx driver to work for about 2 months now, and it has, up until today, worked for me every time I've needed it.  

Today however, it is not working.  After I do the driver-select alx, and go and enter make, it errors out.  

```
bonez@Utopia:~/compat-wireless-3.6.6-1-snpc$ ./scripts/driver-select alx
Processing new driver-select request...
Backing up makefile: Makefile.bk
Backup exists: Makefile.bk
Backing up makefile: drivers/net/ethernet/broadcom/Makefile.bk
Backing up makefile: drivers/net/ethernet/atheros/Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: drivers/net/ethernet/broadcom/Makefile.bk
bonez@Utopia:~/compat-wireless-3.6.6-1-snpc$ make
./scripts/gen-compat-autoconf.sh /home/bonez/compat-wireless-3.6.6-1-snpc/.config /home/bonez/compat-wireless-3.6.6-1-snpc/config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/3.5.0-17-generic/build M=/home/bonez/compat-wireless-3.6.6-1-snpc modules
make: *** /lib/modules/3.5.0-17-generic/build: No such file or directory.  Stop.
make: *** [modules] Error 2

```

I tried this first on a fresh ubuntu install which I had not updated yet, and I thought that was the problem.  So i did another install on another partition, but let the installer run updates while installing.  I followed your steps and got the same error.  

I also tried downloading a newer version of the driver, the 3.6 version, from the same site, and still have the same error when I enter "make".  Any ideas?  This is really frustrating because my wireless speeds are like 50 - 75 kb/s max.

---

### Post by chili555 on 2012-11-12
This version makes perfectly on my 3.5.0.18 system: [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.4-1-snpc.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.4-1-snpc.tar.bz2)

---

### Post by KFwLsKvVAs on 2012-11-12
Thanks for the quick reply.  Unfortunately I get the same make error with that version too.  

```
bonez@Utopia:~/compat-wireless-3.5.4-1-snpc$ make
./scripts/gen-compat-autoconf.sh /home/bonez/compat-wireless-3.5.4-1-snpc/.config /home/bonez/compat-wireless-3.5.4-1-snpc/config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/3.5.0-17-generic/build M=/home/bonez/compat-wireless-3.5.4-1-snpc modules
make: *** /lib/modules/3.5.0-17-generic/build: No such file or directory.  Stop.
make: *** [modules] Error 2
bonez@Utopia:~/compat-wireless-3.5.4-1-snpc$ 

```

Is it possible that the original makefile that got created when I did driver-select for the 3.5.1-1 version is somehow affecting the newer versions?  I notice that when I do driver-select with either of the newer versions it says this:

```
bonez@Utopia:~/compat-wireless-3.5.4-1-snpc$ ./scripts/driver-select alx
Processing new driver-select request...
Backing up makefile: Makefile.bk
Backup exists: Makefile.bk
Backing up makefile: drivers/net/ethernet/broadcom/Makefile.bk
Backing up makefile: drivers/net/ethernet/atheros/Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: drivers/net/ethernet/broadcom/Makefile.bk

```

---

### Post by chili555 on 2012-11-12
Please be sure you have linux-headers-generic and build-essential installed. I'd check in Software Manager or Synaptic and install as needed. Then try again:```
./scripts/driver-select restore
make clean
./scripts/driver-select alx
make  [COLOR="Red"]<--and if there are no errors[/COLOR]
sudo make install

```

---

### Post by KFwLsKvVAs on 2012-11-12
I had tried installing linux-headers-generic and build-essential initially, and they installed correctly, but then I got that make error.  

I went into synaptic and searched linux-headers, and installed a few different headers before it finally worked, but that did the trick.  Thanks for the help.

---

### Post by kurru on 2012-11-17
Many thanks Chili555! This is working fine on my Lenovo g780 with same Atheros chip.

---

### Post by younussalimpv on 2012-11-19
Wow chili555

It's really a wonderful job. I used an extra ethernet card as the onboard one is Atheros. But I'm really glad that it's high time to remove the extra and help others also getting connected through Athros

Thank You !

---

### Post by benhuan on 2012-11-26
> **chili555 said:**
> Your device works with the elusive driver *alx*. My long delay in responding was because I was working out how and where to get it working. It will require big downloads and we'll need to get your wireless working first. Do you have an available wireless network you can connect to?You have the driver in place and I assume the wireless is disabled because the switch is set to OFF. Confirm:```
rfkill list all
```Flip it to ON and get an internet connection. Then open a terminal and do:```
sudo apt-get install linux-headers-generic build-essential
wget http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.1-1-snpc.tar.bz2
tar -xf compat-wireless-3.5.1-1-snpc.tar.bz2
cd compat-wireless-3.5.1-1-snpc
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx
```Your wired ethernet should now be working.


:guitar:Thank you so much . It works well.

---

### Post by dextre1480 on 2012-11-29
> **chili555 said:**
> Woo hoo! That is awesome news! Great job.

As with any driver or module that's compiled from source code, it was compiled against your running kernel version only. When you get updates and get a newer kernel version, also known as linux-image, you will need to recompile:```
cd Desktop/compat-wireless-3.5.1-1-snpc
make clean
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx
```You might copy these instructions to your desktop so you'll recall when the time comes.

The *alx* driver is a new arrival and you've worked out a successful install. So the searchers can find the fix, please use thread tools at the top and mark Solved.
hello chili555 thak you too much because i had that problem too, but thaks to you i coud resolved this one, i have a laptop lenovo g480 with intel 64bit, and ubuntu 12.04 did not take the ethernet atheros ar8162, just 
sudo apt-get install linux-headers-generic build-essential 
wget [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.1-1-snpc.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.1-1-snpc.tar.bz2) 
tar -xf compat-wireless-3.5.1-1-snpc.tar.bz2 
cd compat-wireless-3.5.1-1-snpc 
./scripts/driver-select alx 
make 
sudo make install 
sudo modprobe alx

aplaying just one by one, gracias amigo chili555 saludos desde Lima-Perú

---

### Post by chili555 on 2012-11-29
Thank you all for your kind comments. Have fun!

---

### Post by jraz001 on 2012-12-15
I wanted to first say thanks as this was truly helpful for me too. I just bought a G580 and many posts on the web showed frustration with this driver. I found one post that almost got it right but yours had the extra detail about build essentials.

Solved for a G580 thanks to chili555. :)

---

### Post by bishop__ on 2012-12-19
Your post really helped me alot! It work! Thanks Chili555!

However, I have observed that if I apply updates from the Ubuntu Update Manager, it seems that the driver is overwritten. 

Is there a way to avoid this to happen? 



> **chili555 said:**
> Your device works with the elusive driver *alx*. My long delay in responding was because I was working out how and where to get it working. It will require big downloads and we'll need to get your wireless working first. Do you have an available wireless network you can connect to?You have the driver in place and I assume the wireless is disabled because the switch is set to OFF. Confirm:```
rfkill list all
```Flip it to ON and get an internet connection. Then open a terminal and do:```
sudo apt-get install linux-headers-generic build-essential
wget http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.1-1-snpc.tar.bz2
tar -xf compat-wireless-3.5.1-1-snpc.tar.bz2
cd compat-wireless-3.5.1-1-snpc
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx
```Your wired ethernet should now be working.

---

### Post by chili555 on 2012-12-19
> **bishop__ said:**
> Your post really helped me alot! It work! Thanks Chili555!

However, I have observed that if I apply updates from the Ubuntu Update Manager, it seems that the driver is overwritten. 

Is there a way to avoid this to happen?Not at present. The driver needs to be recompiled when a newer linux-image is installed. Ordinary updates, Firefox, gedit, VLC, for example, don't require a recompile. The proper procedure is:```
cd compat-wireless-3.5.1-1-snpc
./scripts/driver-select alx
[COLOR="Red"]make clean[/COLOR]
make 
sudo make install
sudo modprobe alx
```Some day soon, we hope, the driver *alx* will be included in the kernel by default.

---

### Post by gitfredy on 2012-12-20
All hail chilli. Finally after setting some permissions it installed the alx driver and thats allowed ethernet access, a lot of chmod 755 went on to get it to do its thing but pretty much the instructions as provided were perfect. I had issues installing some of the headers/build essentials but I did it 1 by 1 and that helped.

thanks again all.

---

### Post by Dytech on 2012-12-23
Hey!

I also got a new notebook with the same network card. I am on a fresh install of ubuntu gnome remix 12.10.1
I only installed firefox and normal system updates.

I tried searching apt-cache and found there was a package:linux-backports-modules-cw-3.6.quantal

so i thought a package is usually better than compiling yourself so i tried that one. Rebooted and now it won't go into runtime level 7. No graphic interface anymore. it seems no displays can be found, tried Xreset, xrandr wont't give any output. No displays found, and all i thought i was doing was installing a network driver :)

How could that happen? Any ideas? And what can i do to fix it. 

Thanks!

---

### Post by chili555 on 2012-12-24
> **Dytech said:**
> Hey!

I also got a new notebook with the same network card. I am on a fresh install of ubuntu gnome remix 12.10.1
I only installed firefox and normal system updates.

I tried searching apt-cache and found there was a package:linux-backports-modules-cw-3.6.quantal

so i thought a package is usually better than compiling yourself so i tried that one. Rebooted and now it won't go into runtime level 7. No graphic interface anymore. it seems no displays can be found, tried Xreset, xrandr wont't give any output. No displays found, and all i thought i was doing was installing a network driver :)

How could that happen? Any ideas? And what can i do to fix it. 

Thanks!You might try, at the command prompt when X won't start:```
sudo apt-get remove --purge linux-backports-modules-cw-3.6.quantal
sudo reboot
```

---

### Post by gitfredy on 2012-12-30
So a week ago I followed your instructions chilli, but I caved and updated ubuntu. So now i'm stuck. The ethernet isn't working again. This is a nooby problem because I can see all the components there but I just don't know how to fix it. I think it might be an issue with linux headers being updated. When I navigate to the older 3.5.0-17-generic folder I can see the 'updates' folder with subfolders 'compat and 'drivers'. So it seems all the stuff is there, but I don't know how to actually "activate" that driver for use again. (post update)

When I try to run the full instructions again as you first suggested I get an error that says 
"make: *** /lib/modules/3.5.0-21-generic/build no such file or directory. stop"
"make: *** [modules] Error 2." 

I suppose there might be a way to point to that driver? My searching has yielded nothing that doesn't ask me to re-install ubuntu. 

Apologies if my post is poor. Thanks in advance all.

---

### Post by chili555 on 2012-12-30
> When I try to run the full instructions again as you first suggested I get an error that says
"make: *** /lib/modules/3.5.0-21-generic/build no such file or directory. stop"
"make: *** [modules] Error 2."
I suspect the linux-headers didn't get updated correctly. It will hopefully be a trivial fix. Hook up the ethernet and do:```
sudo apt-get install --reinstall linux-headers-generic linux-headers-`uname -r`
```Those backticks are on the left side of my US keyboard on the same key with ~.

Then re-compile the driver.

---

### Post by gitfredy on 2012-12-30
Hi, 

Thanks for the quick reply, appreciate it. I should have noted that my wireless doesn't work (but this is because of school network issues) and I tried plugging the ethernet but I get the "unable to fetch some archives"

Also, I have the .deb and tried reinstalling that before as well, but no luck. Could I just remove the newer directory and force it to use the older headers? It seems this would 'cause a lot of problems from what I've gathered in searching.

Enother edit: the 'build' folder has a little arrow pointing out of it. I suppose this is a link? something to do with "ln" command but i'm not familiar with it. I will try to link to that folder, but that may be an issue because it might be linked to something else. Not sure.

yeah that build folder in 3.5.0-17-generic is linked to "inode/directory"

thanks again, will post if I get anywhere.

---

### Post by chili555 on 2012-12-30
> Also, I have the .debWhich .deb is that? I thought you were installing from the downloaded tar.bz2. > Could I just remove the newer directory and force it to use the older headers? It seems this would 'cause a lot of problems from what I've gathered in searching. Yes, indeed; many problems. Not the least of which is that the driver wouldn't compile anyway.

You could go here and download the packages and transfer them on a USB key: [http://packages.ubuntu.com/quantal/linux-headers-generic](http://packages.ubuntu.com/quantal/linux-headers-generic)

Be sure to get both -generic and 3.5.0-21. Be sure to get your architecture correct; either 32- or 64-bit:```
arch
```After you get them to your desktop, install:```
cd Desktop
sudo dpkg -i linux*.deb
```Then re-compile.

---

### Post by gitfredy on 2012-12-30
Update/Edit:

Ok, it's working now. The updates just 'updates' the regular ol' linux-headers-3.5.0-xx and not the linux-headers-3.5.0-xx-generic so as per your suggestions I made sure both are installed under usr/src. Thanks again sir, and I wish you an excellent weekend. did make clean first then recompiled as well after installing the generic.


I have the linux-headers-3.5 [....] 3.5.0-21.32_all.deb file, I figured this contained everything (this is what I reinstalled again, and I think was installed in the update.. Sorry for the bother, but could you point me to the 3.5.0.21 (the non-generic one). 

When I look under usr/src I see the two different folder "linux-headers-3.5.0-17" and "linux-headers-3.5.0-17-generic" but for the "linux-headers-3.5.0-21" I don't see an equivalent generic folder.

---

### Post by chili555 on 2012-12-30
> When I look under usr/src I see the two different folder "linux-headers-3.5.0-17" and "linux-headers-3.5.0-17-generic" but for the "linux-headers-3.5.0-21" I don't see an equivalent generic folder.
You will have everything you need if you did:```
sudo apt-get install --reinstall linux-headers-generic linux-headers-`uname -r`
```...as above.

Glad it's working!

---

### Post by batpat on 2013-01-10
Hi, thank you for the nice guide, 
i have an Gigabyte GA-H77M-D3H (Chipsatz: H77/mATX) Mainboard with an Atheros AR8161 Lanchip without wlan. I followed your prozedure and used the latest driver compat-wireless-3.6.8-1-snp. But something with alx is wrong. I am totaly new in Linux  (3.5.0-17-generic, x86_64) and installed Kubuntu 12.10 via Win 7 and Wubi ([http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer))

What made i wrong, and how do i solve the problem :)?

thank you for anny tipps.
batpat


Terminaloutput:

batpat@ubuntu:~$  ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7600 (7.6 KB)  TX bytes:7600 (7.6 KB)

batpat@ubuntu:~$ sudo lshw -C network
[sudo] password for batpat: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR8161 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:f7100000-f713ffff ioport:d000(size=128)
batpat@ubuntu:~$ lspci -nn | grep 0200
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091] (rev 10)
batpat@ubuntu:~$ arch
x86_64
batpat@ubuntu:~$ uname -r
3.5.0-17-generic
batpat@ubuntu:~$ cd Arbeitsfläche
batpat@ubuntu:~/Arbeitsfläche$ cd compat-wireless-3.6.8-1-snpc/
batpat@ubuntu:~/Arbeitsfläche/compat-wireless-3.6.8-1-snpc$ ./scripts/driver-select 
code-metrics.txt                                .gitignore
compat/                                         include/
.compat_autoconf_compat-wireless-v3.6.8-1-snpc  linux-next-cherry-picks/
.compat_base                                    linux-next-pending/
.compat_base_tree                               MAINTAINERS
.compat_base_tree_version                       Makefile
.compat_version                                 Makefile.bk
.config                                         net/                                                                                 
config.mk                                       patches/                                                                             
.config.mk_md5sum.txt                           pending-stable/                                                                      
COPYRIGHT                                       README                                                                               
crap/                                           scripts/                                                                             
defconfigs/                                     .tmp_versions/                                                                       
drivers/                                        udev/                                                                                
enable-older-kernels/                                                                                                                
batpat@ubuntu:~/Arbeitsfläche/compat-wireless-3.6.8-1-snpc$ ./scripts/driver-select alx
Processing new driver-select request...                                                                                              
Backup exists: Makefile.bk                                                                                                           
Backup exists: Makefile.bk                                                                                                           
Backup exists: drivers/net/ethernet/broadcom/Makefile.bk                                                                             
Backup exists: drivers/net/ethernet/atheros/Makefile.bk                                                                              
Backup exists: Makefile.bk                                                                                                           
Backup exists: Makefile.bk                                                                                                           
Backup exists: drivers/net/ethernet/broadcom/Makefile.bk                                                                             
batpat@ubuntu:~/Arbeitsfläche/compat-wireless-3.6.8-1-snpc$ make                                                                 
make -C /lib/modules/3.5.0-17-generic/build M=/home/batpat/Arbeitsfläche/compat-wireless-3.6.8-1-snpc modules                    
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-17-generic'                                                                
/usr/src/linux-headers-3.5.0-17-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support                        
make[1]: gcc: Command not found                                                                                                      
make[2]: gcc: Command not found                                                                                                      
make[2]: gcc: Command not found                                                                                                      
  CC [M]  /home/batpat/Arbeitsfläche/compat-wireless-3.6.8-1-snpc/compat/main.o
/bin/sh: 1: gcc: not found
make[3]: *** [/home/batpat/Arbeitsfläche/compat-wireless-3.6.8-1-snpc/compat/main.o] Error 127
make[2]: *** [/home/batpat/Arbeitsfläche/compat-wireless-3.6.8-1-snpc/compat] Error 2
make[1]: *** [_module_/home/batpat/Arbeitsfläche/compat-wireless-3.6.8-1-snpc] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-17-generic'
make: *** [modules] Error 2
batpat@ubuntu:~/Arbeitsfläche/compat-wireless-3.6.8-1-snpc$ sudo make install
sudUpdating Ubuntu's initramfs for 3.5.0-17-generic under /boot/ ...
Warning: No support for locale: de_DE.utf8
Will now run update-grub to ensure grub will find the new initramfs ...
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Found Windows 7 (loader) on /dev/sda1
Skipping Windows 7 (loader) on Wubi system
done

make -C /lib/modules/3.5.0-17-generic/build M=/home/batpat/Arbeitsfläche/compat-wireless-3.6.8-1-snpc modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-17-generic'
/usr/src/linux-headers-3.5.0-17-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
make[1]: gcc: Command not found
make[2]: gcc: Command not found
make[2]: gcc: Command not found
  CC [M]  /home/batpat/Arbeitsfläche/compat-wireless-3.6.8-1-snpc/compat/main.o
/bin/sh: 1: gcc: not found
make[3]: *** [/home/batpat/Arbeitsfläche/compat-wireless-3.6.8-1-snpc/compat/main.o] Error 127
make[2]: *** [/home/batpat/Arbeitsfläche/compat-wireless-3.6.8-1-snpc/compat] Error 2
make[1]: *** [_module_/home/batpat/Arbeitsfläche/compat-wireless-3.6.8-1-snpc] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-17-generic'
make: *** [modules] Error 2
batpat@ubuntu:~/Arbeitsfläche/compat-wireless-3.6.8-1-snpc$ sudo modprobe alx
FATAL: Module alx not found.

---

### Post by chili555 on 2013-01-10
> make: *** [modules] Error 2When you get an error at 'make' then make install isn't going to work, modprobe isn't going to work and the driver won't work. You may as well save yourself the trouble and stop and fix it first.> make[1]: gcc: Command not found
make[2]: gcc: Command not found
make[2]: gcc: Command not found That usually tells us that the necessary prerequisites are not installed.```
sudo apt-get install build-essential
```If you have no internet connection, you can follow the outline here: [http://ubuntuforums.org/showpost.php?p=12448318&postcount=105](http://ubuntuforums.org/showpost.php?p=12448318&postcount=105) All you need worry about is the build-essential part. Note that one of the dependencies of build-essential is gcc!

[http://packages.ubuntu.com/quantal/build-essential](http://packages.ubuntu.com/quantal/build-essential)

Be sure to download either 32- or 64-bit as appropriate. Once you have build-essential installed, try alx again and I'm quite confident it will install.

---

### Post by Shabakthanai on 2013-01-13
I was just here to learn.  What an elite piece of help was provided.  It was a pleasure to view this post.  Cudos!

---

### Post by jeeptrash on 2013-01-13
> **KFwLsKvVAs said:**
> Chili555,

I've been using your instructions for getting the alx driver to work for about 2 months now, and it has, up until today, worked for me every time I've needed it.  

Today however, it is not working.  After I do the driver-select alx, and go and enter make, it errors out.  

```
bonez@Utopia:~/compat-wireless-3.6.6-1-snpc$ ./scripts/driver-select alx
Processing new driver-select request...
Backing up makefile: Makefile.bk
Backup exists: Makefile.bk
Backing up makefile: drivers/net/ethernet/broadcom/Makefile.bk
Backing up makefile: drivers/net/ethernet/atheros/Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: drivers/net/ethernet/broadcom/Makefile.bk
bonez@Utopia:~/compat-wireless-3.6.6-1-snpc$ make
./scripts/gen-compat-autoconf.sh /home/bonez/compat-wireless-3.6.6-1-snpc/.config /home/bonez/compat-wireless-3.6.6-1-snpc/config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/3.5.0-17-generic/build M=/home/bonez/compat-wireless-3.6.6-1-snpc modules
make: *** /lib/modules/3.5.0-17-generic/build: No such file or directory.  Stop.
make: *** [modules] Error 2

```

I tried this first on a fresh ubuntu install which I had not updated yet, and I thought that was the problem.  So i did another install on another partition, but let the installer run updates while installing.  I followed your steps and got the same error.  

I also tried downloading a newer version of the driver, the 3.6 version, from the same site, and still have the same error when I enter "make".  Any ideas?  This is really frustrating because my wireless speeds are like 50 - 75 kb/s max.



Alright, i know this thread is marked solved but i will try anyway.

I have a AR8161 ethernet adapter and i can not get it to work, i am getting the same error 2 that is posted above.  I believe i have done everything correct that is posted in the original fix, seeing how i can't connect to the internet it made it a little tedious.  I tried installing the different packages at least 3-4 times each.  How many .deb files should i have downloaded?  Seems like the error is in the making.

What am i missing? Is it since my model is slightly different that it doesnt work or what?  Would it be easier to get my wireless adapter working or is it all in the same?

Would it be worth while to pickup a cheap usb Ethernet adapter that's supported so i can just run the commands and download and install everything i need?

Thanks in advance for any input!

---

### Post by chili555 on 2013-01-13
> /lib/modules/3.5.0-17-generic/build: No such file or directory.  Stop.That usually means you don't have linux-headers installed. What is your version?```
arch
uname -r
```We can probably get it on a USB key quicker than you could drive to the store!> Would it be easier to get my wireless adapter working or is it all in the same?Exactly. Each is probably as difficult as the other.

---

### Post by jeeptrash on 2013-01-13
> **chili555 said:**
> That usually means you don't have linux-headers installed. What is your version?```
arch
uname -r
```We can probably get it on a USB key quicker than you could drive to the store!Exactly. Each is probably as difficult as the other.

arch

```
x86_64
```

uname -r

```
3.5.0-17-generic
```


Your quick to reply, that's great!

---

### Post by chili555 on 2013-01-13
[http://packages.ubuntu.com/quantal/linux-headers-3.5.0-17-generic](http://packages.ubuntu.com/quantal/linux-headers-3.5.0-17-generic)
[http://packages.ubuntu.com/quantal/libc6](http://packages.ubuntu.com/quantal/libc6)
[http://packages.ubuntu.com/quantal/linux-headers-3.5.0-17](http://packages.ubuntu.com/quantal/linux-headers-3.5.0-17) (no amd64; get 'all')

Get these packages and be sure to click the amd64 version, also known as 64-bit. Get it to your desktop and install from a terminal:```
cd Desktop
sudo dpkg -i linux-headers*.deb
sudo dpkg -i libc6*.deb
```Then run your compile again and I suspect it will succeed.

Off for the evening. They allow me a bit of rest after 18 hours!

---

### Post by jeeptrash on 2013-01-13
> **chili555 said:**
> [http://packages.ubuntu.com/quantal/linux-headers-3.5.0-17-generic](http://packages.ubuntu.com/quantal/linux-headers-3.5.0-17-generic)
[http://packages.ubuntu.com/quantal/libc6](http://packages.ubuntu.com/quantal/libc6)
[http://packages.ubuntu.com/quantal/linux-headers-3.5.0-17](http://packages.ubuntu.com/quantal/linux-headers-3.5.0-17) (no amd64; get 'all')

Get these packages and be sure to click the amd64 version, also known as 64-bit. Get it to your desktop and install from a terminal:```
cd Desktop
sudo dpkg -i linux-headers*.deb
sudo dpkg -i libc6*.deb
```Then run your compile again and I suspect it will succeed.

Off for the evening. They allow me a bit of rest after 18 hours!



Alright here's what i have now.  Dont think the whole output is important for me to type out.  Upon the command make i am getting quite a lot of gcc Command not found errors, and at the end a modules error 2.

Going back over it again it seems like I may have had a problem installing build essentials possibly? When i try to install it again i get dependency errors, and it says libc6-dev:amd64 is not configured yet, and libc-dev is not installed.  When i try to install libc6-dev:amd64 i also get errors.

I would love to be able to copy and paste it for you :lolflag:

Start me off on what to do next it would be great! i'm quite stubborn and i will get this working.  I do have basic linux knowledge but defiantly not enough to get through this myself.

Oh, and the three files you mentioned installed fine.

---

### Post by chili555 on 2013-01-14
> **jeeptrash said:**
> Alright here's what i have now.  Dont think the whole output is important for me to type out.  Upon the command make i am getting quite a lot of gcc Command not found errors, and at the end a modules error 2.

Going back over it again it seems like I may have had a problem installing build essentials possibly? When i try to install it again i get dependency errors, and it says libc6-dev:amd64 is not configured yet, and libc-dev is not installed.  When i try to install libc6-dev:amd64 i also get errors.

I would love to be able to copy and paste it for you :lolflag:

Start me off on what to do next it would be great! i'm quite stubborn and i will get this working.  I do have basic linux knowledge but defiantly not enough to get through this myself.

Oh, and the three files you mentioned installed fine.The general process is to go get the missing packages and install them as above until you have no further dependency errors. Without an internet connection, I know it is a tedious task that hardly ever goes perfectly the first try.

If you can't see what to download and install, you can copy and paste the errors from the terminal into a text document using Gedit; name it make_error.txt and transfer it on a USB key and then post it here. If it is very long, post it here and give us the link: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Keep on going; you are doing very well.

---

### Post by jeeptrash on 2013-01-14
> **chili555 said:**
> The general process is to go get the missing packages and install them as above until you have no further dependency errors. Without an internet connection, I know it is a tedious task that hardly ever goes perfectly the first try.

If you can't see what to download and install, you can copy and paste the errors from the terminal into a text document using Gedit; name it make_error.txt and transfer it on a USB key and then post it here. If it is very long, post it here and give us the link: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Keep on going; you are doing very well.

Alright, this was my quick attempt before heading to work for the day.


```
jeeptrash@destroyer:~/Desktop$ sudo dpkg -i gcc-4.7*.deb
(Reading database ... 167272 files and directories currently installed.)
Preparing to replace gcc-4.7-base:amd64 4.7.2-2ubuntu1 (using gcc-4.7-base_4.7.2-2ubuntu1_amd64.deb) ...
Unpacking replacement gcc-4.7-base:amd64 ...
Setting up gcc-4.7-base:amd64 (4.7.2-2ubuntu1) ...
jeeptrash@destroyer:~/Desktop$ cd com*
jeeptrash@destroyer:~/Desktop/compat-wireless-3.5.1-1-snpc$ ./scripts/driver-select alx
Processing new driver-select request...
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: drivers/net/ethernet/broadcom/Makefile.bk
Backup exists: drivers/net/ethernet/atheros/Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: drivers/net/ethernet/broadcom/Makefile.bk
jeeptrash@destroyer:~/Desktop/compat-wireless-3.5.1-1-snpc$ make
make -C /lib/modules/3.5.0-17-generic/build M=/home/jeeptrash/Desktop/compat-wireless-3.5.1-1-snpc modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-17-generic'
/usr/src/linux-headers-3.5.0-17-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
make[1]: gcc: Command not found
make[2]: gcc: Command not found
make[2]: gcc: Command not found
  CC [M]  /home/jeeptrash/Desktop/compat-wireless-3.5.1-1-snpc/compat/main.o
/bin/sh: 1: gcc: not found
make[3]: *** [/home/jeeptrash/Desktop/compat-wireless-3.5.1-1-snpc/compat/main.o] Error 127
make[2]: *** [/home/jeeptrash/Desktop/compat-wireless-3.5.1-1-snpc/compat] Error 2
make[1]: *** [_module_/home/jeeptrash/Desktop/compat-wireless-3.5.1-1-snpc] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-17-generic'
make: *** [modules] Error 2







```When i run print for build essentials i get this, assuming these are the packages i need?  


```
jeeptrash@destroyer:~/Desktop/compat-wireless-3.5.1-1-snpc$ apt-get install --print-uris build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 build-essential : Depends: g++ (>= 4:4.4.3) but it is not installable
 cpp : Depends: cpp-4.6 (>= 4.6.3-1~) but it is not installable
 dpkg-dev : Depends: libdpkg-perl (= 1.16.1.2ubuntu7) but 1.16.7ubuntu6 is to be installed
            Recommends: fakeroot but it is not installable
            Recommends: libalgorithm-merge-perl but it is not installable
 gcc : Depends: gcc-4.6 (>= 4.6.3-1~) but it is not installable
 libc6 : Depends: libc-bin (= 2.15-0ubuntu20) but 2.15-0ubuntu10.2 is to be installed
 libc6-dev : Depends: libc6 (= 2.15-0ubuntu10.2) but 2.15-0ubuntu20 is to be installed
             Depends: libc-dev-bin (= 2.15-0ubuntu10.2) but 2.15-0ubuntu20 is to be installed
 linux-backports-modules-cw-3.4-precise-generic : Depends: linux-backports-modules-cw-3.4-3.2.0-36-generic but it is not installable
 linux-headers-3.2.0-35-generic : Depends: linux-headers-3.2.0-35 but it is not installable
 linux-headers-3.5.0-22-generic : Depends: linux-headers-3.5.0-22 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
jeeptrash@destroyer:~/Desktop/compat-wireless-3.5.1-1-snpc$ 





```



How to proceed?

---

### Post by chili555 on 2013-01-14
[http://packages.ubuntu.com/quantal/build-essential](http://packages.ubuntu.com/quantal/build-essential)

Grab all these 'depends' (red dots) and install them. Some of them may not install because they have unmet dependencies; install their dependencies, too. Rinse and repeat. Eventually, you will get build-essential completely installed. Then try your compile again. 

It appears you have a 64-bit system; be sure you get the 'amd64' versions, or if there is no distinction, 'all.'

---

### Post by jeeptrash on 2013-01-14
> **chili555 said:**
> [http://packages.ubuntu.com/quantal/build-essential](http://packages.ubuntu.com/quantal/build-essential)

Grab all these 'depends' (red dots) and install them. Some of them may not install because they have unmet dependencies; install their dependencies, too. Rinse and repeat. Eventually, you will get build-essential completely installed. Then try your compile again. 

It appears you have a 64-bit system; be sure you get the 'amd64' versions, or if there is no distinction, 'all.'

Alright, i have gotten a few errors out of the way but i am stuck here.

If i read this right, it is telling me that it can not install the package i am trying to install because it depends on the package i am trying to install?  Or am i missing something and reading it wrong.

```
jeeptrash@destroyer:~/Desktop$ sudo dpkg -i g++_4.7.2-1ubuntu2_amd64.deb
(Reading database ... 167299 files and directories currently installed.)
Preparing to replace g++ 4:4.7.2-1ubuntu2 (using g++_4.7.2-1ubuntu2_amd64.deb) ...
Unpacking replacement g++ ...
dpkg: dependency problems prevent configuration of g++:
 g++ depends on g++-4.7 (>= 4.7.2-1~); however:
  Package g++-4.7 is not installed.

dpkg: error processing g++ (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 g++



```

---

### Post by jeeptrash on 2013-01-15
Here is where i got to tonight.  I can not get any of these packages to install. I feel i am dead in the water, i have tried each of them multiple times.  Here is the now shortened print from build essentials.

```
jeeptrash@destroyer:~/Desktop$ apt-get install --print-uris build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 g++ : Depends: g++-4.7 (>= 4.7.2-1~) but it is not installable
 linux-backports-modules-cw-3.4-precise-generic : Depends: linux-backports-modules-cw-3.4-3.2.0-36-generic but it is not installable
 linux-headers-3.2.0-35-generic : Depends: linux-headers-3.2.0-35 but it is not installable
 linux-headers-3.5.0-22-generic : Depends: linux-headers-3.5.0-22 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
jeeptrash@destroyer:~/Desktop$ 


```

I think i may have 2 extra versions of linux headers installed?  My uname -r is ```
3.5.0-17-generic
```.  Which i believe is installed correctly.

I feel that i am close, but am doing something wrong and can't see what it is.


Would running this help me out? Don't want to take a step backwards. ```
apt-get -f install
```

---

### Post by chili555 on 2013-01-15
> Would running this help me out? Don't want to take a step backwards.
```
apt-get -f install
```

It would help and it would fix everything if you had internet access to download packages, which you don't...yet! So let's not.> g++ depends on g++-4.7 (>= 4.7.2-1~); however:
  Package g++-4.7 is not installed.If you click on g++ in my link, you can download it: g++_4.7.2-1ubuntu2_amd64.deb. However, please note that it also has dependencies, one of which is g++-4.7. [http://packages.ubuntu.com/quantal/g++-4.7](http://packages.ubuntu.com/quantal/g++-4.7)

Get it and install it. Then try again to install g++_4.7.2-1ubuntu2_amd64.deb and then I'm not sure I'd try backports.I am not sure it contains alx. I'd compile compat-wireless-3.6.6-1-snpc as above. I *know* it's included there.

---

### Post by jeeptrash on 2013-01-15
> **chili555 said:**
> It would help and it would fix everything if you had internet access to download packages, which you don't...yet! So let's not.If you click on g++ in my link, you can download it: g++_4.7.2-1ubuntu2_amd64.deb. However, please note that it also has dependencies, one of which is g++-4.7. [http://packages.ubuntu.com/quantal/g++-4.7](http://packages.ubuntu.com/quantal/g++-4.7)

Get it and install it. Then try again to install g++_4.7.2-1ubuntu2_amd64.deb and then I'm not sure I'd try backports.I am not sure it contains alx. I'd compile compat-wireless-3.6.6-1-snpc as above. I *know* it's included there.


I greatly appreciate your patience with me, i do understand what i need to do installing all the dependencies in theory but i just can't quite get it.  

This has me stumped, in order to get libstdc++6-4.7-dev_4.7.2-2ubuntu1_amd64.deb installed it depends on g++-4.7_4.7.2-2ubuntu1_amd64.deb  So they both depend on each other and I can not install either one?


```
jeeptrash@destroyer:~/Desktop$ sudo dpkg -i libstdc++6-4.7-dev_4.7.2-2ubuntu1_amd64.deb
(Reading database ... 168055 files and directories currently installed.)
Preparing to replace libstdc++6-4.7-dev 4.7.2-2ubuntu1 (using libstdc++6-4.7-dev_4.7.2-2ubuntu1_amd64.deb) ...
Unpacking replacement libstdc++6-4.7-dev ...
dpkg: dependency problems prevent configuration of libstdc++6-4.7-dev:
 libstdc++6-4.7-dev depends on g++-4.7 (= 4.7.2-2ubuntu1); however:
  Package g++-4.7 is not configured yet.

dpkg: error processing libstdc++6-4.7-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libstdc++6-4.7-dev
jeeptrash@destroyer:~/Desktop$ sudo dpkg -i g++-4.7_4.7.2-2ubuntu1_amd64.deb
(Reading database ... 168055 files and directories currently installed.)
Preparing to replace g++-4.7 4.7.2-2ubuntu1 (using g++-4.7_4.7.2-2ubuntu1_amd64.deb) ...
Unpacking replacement g++-4.7 ...
dpkg: dependency problems prevent configuration of g++-4.7:
 g++-4.7 depends on libstdc++6-4.7-dev (= 4.7.2-2ubuntu1); however:
  Package libstdc++6-4.7-dev is not configured yet.

dpkg: error processing g++-4.7 (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 g++-4.7
jeeptrash@destroyer:~/Desktop$ 



```

---

### Post by Basti890 on 2013-01-16
Please Help me!
I have the same Problem, but when i try to install the packages i can't find the right Linux-headers for my distribution (new Ubuntu 12.10) x86_64 with 3.5.0-17-generic as kernel.

can anyone help me please?

&#8364;dit: when i try **apt-get install build-essential linux-headers-generic linux-headers-3.5.0-17-generic**
> sebastian@sebastian-HP-Elite-7500-Series-MT:/media/sebastian/0000-0001$ sudo apt-get install build-essential linux-headers-generic linux-headers-3.5.0-17-generic
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
linux-headers-3.5.0-17-generic ist schon die neueste Version.
build-essential ist schon die neueste Version.
linux-headers-generic ist schon die neueste Version.
Probieren Sie »apt-get -f install«, um dies zu korrigieren:
Die folgenden Pakete haben unerfüllte Abhängigkeiten:
 g++-4.6 : Hängt ab von: gcc-4.6-base (= 4.6.3-10ubuntu1) aber 4.6.3-1ubuntu5 soll installiert werden
 gcc-4.6 : Hängt ab von: gcc-4.6-base (= 4.6.3-10ubuntu1) aber 4.6.3-1ubuntu5 soll installiert werden
           Hängt ab von: cpp-4.6 (= 4.6.3-10ubuntu1) aber 4.6.3-1ubuntu5 soll installiert werden
 libc6 : Hängt ab von: libc-bin (= 2.15-0ubuntu10.2) aber 2.15-0ubuntu20 soll installiert werden
 libstdc++6-4.6-dev : Hängt ab von: gcc-4.6-base (= 4.6.3-10ubuntu1) aber 4.6.3-1ubuntu5 soll installiert werden
 linux-headers-generic : Hängt ab von: linux-headers-3.2.0-35-generic ist aber nicht installierbar
 linux-headers-generic-lts-quantal : Hängt ab von: linux-headers-3.5.0-21-generic ist aber nicht installierbar
E: Unerfüllte Abhängigkeiten. Versuchen Sie »apt-get -f install« ohne Angabe eines Pakets (oder geben Sie eine Lösung an).


---

### Post by chili555 on 2013-01-16
> **jeeptrash said:**
> I greatly appreciate your patience with me, i do understand what i need to do installing all the dependencies in theory but i just can't quite get it.  

This has me stumped, in order to get libstdc++6-4.7-dev_4.7.2-2ubuntu1_amd64.deb installed it depends on g++-4.7_4.7.2-2ubuntu1_amd64.deb  So they both depend on each other and I can not install either one?You might try putting both in the same command:```
sudo dpkg -i libstdc++6-4.7-dev*.deb g++-4.7*.deb
```If that won't work, install the first one ignoring dependencies:```
sudo dpkg -i --ignore-depends libstdc++6-4.7-dev*.deb
```Then the other should slide in smoothly.

---

### Post by chili555 on 2013-01-16
> **Basti890 said:**
> Please Help me!
I have the same Problem, but when i try to install the packages i can't find the right Linux-headers for my distribution (new Ubuntu 12.10) x86_64 with 3.5.0-17-generic as kernel.

can anyone help me please?

€dit: when i try **apt-get install build-essential linux-headers-generic linux-headers-3.5.0-17-generic**Usually it is enough to simply do:```
sudo apt-get install build-essential linux-headers-generic
```The *-generic* package is supposed to work out all the dependency issues for you. Please try it.

---

### Post by jeeptrash on 2013-01-16
> **chili555 said:**
> You might try putting both in the same command:```
sudo dpkg -i libstdc++6-4.7-dev*.deb g++-4.7*.deb
```If that won't work, install the first one ignoring dependencies:```
sudo dpkg -i --ignore-depends libstdc++6-4.7-dev*.deb
```Then the other should slide in smoothly.


I thought for sure that would do it!  I tired both *.debs with the same output.

```
jeeptrash@destroyer:~/Desktop$ sudo dpkg -i --ignore-depends libstdc++6-4.7-dev_4.7.2-2ubuntu1_amd64.deb
dpkg: error: --install needs at least one package archive file argument

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through `less' or `more' !


```

---

### Post by chili555 on 2013-01-16
Perhaps I have it backwards, please try:```
sudo dpkg --ignore-depends -i libstdc++6-4.7-dev*.deb
```Or...```
sudo dpkg --force-depends -i libstdc++6-4.7-dev*.deb
```

---

### Post by jeeptrash on 2013-01-16
> **chili555 said:**
> ```
sudo dpkg --force-depends -i libstdc++6-4.7-dev*.deb
```


I am in your debt, Sir.  This worked and i was only missing those 2 .debs. Still a little puzzled why neither of them wouldn't install. Ethernet is working well now.

Now for the wireless drivers, which should be much easier now that i am online.

One last question, should these drivers stay in place with future updates or will it need attention if i run the auto updater?

---

### Post by chili555 on 2013-01-17
> **jeeptrash said:**
> 

One last question, should these drivers stay in place with future updates or will it need attention if i run the auto updater?An excellent question, young Jedi! As with any driver or module that's compiled from source code, it was compiled against your running kernel version only. When you get updates and get a newer kernel version, also known as linux-image, you will need to recompile:
```
cd Desktop/compat-wireless-3.5.1-1-snpc [COLOR="Red"]<--or whichever version you compiled[/COLOR]
make clean
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx

```
You might copy these instructions to your desktop so you'll recall when the time comes.

---

### Post by Basti890 on 2013-01-18
> **chili555 said:**
> Usually it is enough to simply do:```
sudo apt-get install build-essential linux-headers-generic
```The *-generic* package is supposed to work out all the dependency issues for you. Please try it.


when i try it it cames: 
```
sebastian@sebastian-HP-Elite-7500-Series-MT:~$ sudo apt-get install build-essential linux-headers-generic
[sudo] password for sebastian: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
build-essential ist schon die neueste Version.
linux-headers-generic ist schon die neueste Version.
Probieren Sie »apt-get -f install«, um dies zu korrigieren:
Die folgenden Pakete haben unerfüllte Abhängigkeiten:
 g++-4.6 : Hängt ab von: gcc-4.6-base (= 4.6.3-10ubuntu1) aber 4.6.3-1ubuntu5 soll installiert werden
 gcc-4.6 : Hängt ab von: gcc-4.6-base (= 4.6.3-10ubuntu1) aber 4.6.3-1ubuntu5 soll installiert werden
           Hängt ab von: cpp-4.6 (= 4.6.3-10ubuntu1) aber 4.6.3-1ubuntu5 soll installiert werden
 libc6 : Hängt ab von: libc-bin (= 2.15-0ubuntu10.2) aber 2.15-0ubuntu20 soll installiert werden
 libstdc++6-4.6-dev : Hängt ab von: gcc-4.6-base (= 4.6.3-10ubuntu1) aber 4.6.3-1ubuntu5 soll installiert werden
 linux-headers-generic : Hängt ab von: linux-headers-3.2.0-35-generic ist aber nicht installierbar
 linux-headers-generic-lts-quantal : Hängt ab von: linux-headers-3.5.0-21-generic ist aber nicht installierbar
E: Unerfüllte Abhängigkeiten. Versuchen Sie »apt-get -f install« ohne Angabe eines Pakets (oder geben Sie eine Lösung an).
```and when i do [B]./scripts/driver-select alx 
[/B]
```
sebastian@sebastian-HP-Elite-7500-Series-MT:/media/sebastian/F042-8A1B/ubuntu/compat-wireless-3.6.8-1$ ./scripts/driver-select alx
bash: ./scripts/driver-select: Permission denied
sebastian@sebastian-HP-Elite-7500-Series-MT:/media/sebastian/F042-8A1B/ubuntu/compat-wireless-3.6.8-1$ sudo ./scripts/driver-select alx
sudo: ./scripts/driver-select: command not found
sebastian@sebastian-HP-Elite-7500-Series-MT:/media/sebastian/F042-8A1B/ubuntu/compat-wireless-3.6.8-1$ sudo -i
root@sebastian-HP-Elite-7500-Series-MT:~# cd /media/sebastian/F042-8A1B/ubuntu/compat-wireless-3.6.8-1/
root@sebastian-HP-Elite-7500-Series-MT:/media/sebastian/F042-8A1B/ubuntu/compat-wireless-3.6.8-1# ./scripts/driver-select alx
-bash: ./scripts/driver-select: Permission denied

```when i install for examble gcc-4.6-base (= 4.6.3-10ubuntu1) it crys aobut other packages, that need 4.6.3-1ubuntu5 :(

please any help?

PS: i downloaded the newest driver from [http://wireless.kernel.org/en/users/Download/stable/#compat-wireless_stable_releases](http://wireless.kernel.org/en/users/Download/stable/#compat-wireless_stable_releases)

---

### Post by chili555 on 2013-01-18
I would try:```
sudo apt-get install --reinstall build-essential
sudo apt-get install --reinstall linux-headers-generic
sudo apt-get install --reinstall linux-headers-`uname -r`
```Those backticks are on the left side of my US keyboard on the same key with ~.> sebastian@sebastian-HP-Elite-7500-Series-MT:/[COLOR="Red"]media/sebastian/F042-8A1B/[/COLOR]ubuntu/compat-wireless-3.6.8-1$ ./scripts/driver-select alx
bash: ./scripts/driver-select: Permission deniedIt looks like you are trying to install off of a CD, DVD or similar. They are read-only. Please drag and drop the compat-wireless package to your desktop and then do:```
cd ~/Desktop/compat-wireless-3.6.8-1
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx
```

---

### Post by bvpp on 2013-01-26
Sir.....
 I have the same problem and i followed your instructions But still i can't access ethernet.
It shows an error also with a red bubble on the top side of my ubuntu desktop. While installing the packages it also shows error in processing dpkg etc so many packages....
Plsss help me

---

### Post by chili555 on 2013-01-26
> While installing the packages it also shows error in processing dpkg etc so many packages....It would help us to know what the errors are.

---

### Post by Hooorus on 2013-01-30
I just want to thaks CHili555

I tried several things, did not work. YOUR STEP BY STEP GUIDE for amaters helped a lot !
I have lan atheros-AR8161

Thanks thanks thanks

---

### Post by paramjeet on 2013-02-05
Hi I am using ubuntu 12.10 on DELL Laptop XPS. I am not able to connect  with Wired Internet. It was working fine just one day before but not  now. Wireless is working. I tried these options discussed earlier but  didn't help me out. Please help me.

---

### Post by chili555 on 2013-02-05
> **paramjeet said:**
> Hi I am using ubuntu 12.10 on DELL Laptop XPS. I am not able to connect  with Wired Internet. It was working fine just one day before but not  now. Wireless is working. I tried these options discussed earlier but  didn't help me out. Please help me.Do you have the exact same ethernet device? Please open a terminal and run and post:```
lspci -nn | grep 0200
```

---

### Post by paramjeet on 2013-02-05
Thanks for your reply.
output is:

16:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)

---

### Post by chili555 on 2013-02-05
> **paramjeet said:**
> Thanks for your reply.
output is:

16:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)You have a whole different device and we needn't clog up this thread, but try this:```
sudo modprobe r8169
```Does your ethernet come to life? If so, please do:```
sudo su
echo r8169 >> /etc/modules
exit
```If that doesn't solve it, please start your own new thread.

---

### Post by paramjeet on 2013-02-05
No, still same issue. There is an icon showing Auto Ethernet but can not connect.

---

### Post by chili555 on 2013-02-05
> **paramjeet said:**
> No, still same issue. There is an icon showing Auto Ethernet but can not connect.Where is your new thread?

---

### Post by paramjeet on 2013-02-06
New thread is:

[http://ubuntuforums.org/showthread.php?t=2112669](http://ubuntuforums.org/showthread.php?t=2112669)

---

### Post by Arjunanda on 2013-03-16
Thanks,
Great instructions. I was able to follow all the way until make, which failed.

```
 
make: *** /lib/modules/3.5.0-23-generic/build: No such file or directory.  Stop.
make: *** [modules] Error 2
user@Sadhu:~/compat-wireless-3.5.1-1-snpc$ ./scripts/driver-select alx

```

(Oh, this was a multi-page thread, I have read only the first one so far. Now reading further..)

---

### Post by SSchuetrumpf on 2013-03-19
I'm having an issue. I have a Toshiba Satellite C855 that I am trying to install the driver for. Same Atheros AR8162 driver. My Ubuntu on this machine is essentially a fresh install. Because neither my wifi nor ethernet work, it's also essentially a partial install since it could not download the updates that are normally downloaded during installation. It's on the 3.5.0-17-generic kernel. 

I've tried to install all the build dependancies through .deb packages. I downloaded the compat-wireless file on another machine and put it on the Toshiba via USB. When it gets to the make portion, it fails and says "make[1] *** No rule to make target `module'. Stop.". Since this happened, I decided to try to build it on a Ubuntu VM that I have on this machine (the one I'm posting from, a MacBook Pro). Unfortunately the kernel on it is 3.5.0-25-generic. But I decided to try anyway. When I moved the alx.ko into /lib/modules/3.5.0-17-generic/kernel/ubuntu/alx/alx.ko (which was essentially where it installed to on the VM) and tried to do modprobe, it just says not found. When I tried to insmod it, I got "Error inserting module alx.ko: -1 Invalid Parameters".


Any ideas on how I could get this working?

Again, I WAS able to get the module to build and install successfully on the VM, but I can't get it working on the Toshiba.


Edit: I just figured out that modprobe couldn't find it because I was putting alx.ko, I tried with just lax and I get "Invalid argument"

Edit 2: I finally got it to build. My /lib/modules/$(shell uname -r) didn't have a build directory, so I made it manually, not realizing it was supposed to be a symlink to /usr/source/linux-headers-$(shell uname -r). So ignore this post.

---

### Post by sheltongenie on 2013-03-21
> **chili555 said:**
> Your device works with the elusive driver *alx*. My long delay in responding was because I was working out how and where to get it working. It will require big downloads and we'll need to get your wireless working first. Do you have an available wireless network you can connect to?You have the driver in place and I assume the wireless is disabled because the switch is set to OFF. Confirm:```
rfkill list all
```Flip it to ON and get an internet connection. Then open a terminal and do:```
sudo apt-get install linux-headers-generic build-essential
wget http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.1-1-snpc.tar.bz2
tar -xf compat-wireless-3.5.1-1-snpc.tar.bz2
cd compat-wireless-3.5.1-1-snpc
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx
```Your wired ethernet should now be working.


Thank you so much! That worked for me, too for my Toshiba Qosmio x870 with Ubuntu 12.10

---

### Post by Arjunanda on 2013-03-22
Yes thanks, this solved the problem for me as well.

I just had to do first
```
 sudo apt-get update; sudo apt-get upgrade; sudo apt-get install linux-headers-generic build-essential 
```

after that, the compile process went throgh nicely, and drive installed succesfully.

---

### Post by chili555 on 2013-03-22
By the way, the module* alx* is included in Ubuntu 12.10 for kernels 3.5.0-24 and beyond. When Update Manager gives you a lot of updates, one of which is the latest linux-image, currently 3.5.0-26, you will no longer need to compile compat-wireless.

---

### Post by Arjunanda on 2013-04-05
Yes,

Update about 2 weeks ago solved my atheros driver problem, and as a bonus, it also fixed the non-functional screen brightness keys.

---

### Post by phelgan on 2013-04-22
Just a note of thanks for this thread. The support given to the original poster helped me solve the same problem with a Atheros 8161 on an ASUS board.

Chili555, you have my gratitude....

---

### Post by Poutrathor on 2013-05-22
@Chili555 

Thank you very much! This was a perfect solution ! My eth controller was probably next iteration but same fix did great.

```
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091] (rev 10)
```

I followed it cmd by cmd and it worked without any issues. 

I only changed versions numbers at

```
wget http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.8-1-snpc.tar.bz2
```

in order to get the current last version on the repository you gave. 

Thank you!

---

### Post by chili555 on 2013-05-22
Glad it's working! Thanks for posting back so a few searchers will know what works.

---

### Post by mabz1121 on 2013-06-06
Have no Ethernet/Wireless internet access. 

mabz@BELL:~$ lspci -nnk | grep -i -A2 net
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)

      Subsystem: Toshiba America Info Systems Device [1179:ff1e]

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]

      Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0723]

mabz@BELL:~$


mabz@BELL:~$ cd Desktop
mabz@BELL:~/Desktop$ sudo dpkg -i *.deb
(Reading database ... 141460 files and directories currently installed.)
Preparing to replace build-essential 11.5ubuntu2 (using build-essential_11.5ubuntu2_amd64.deb) ...
Unpacking replacement build-essential ...
Preparing to replace cpp 4:4.6.3-1ubuntu5 (using cpp_4.6.3-1ubuntu5_amd64.deb) ...
Unpacking replacement cpp ...
Preparing to replace deb-gview 0.2.8ubuntu3 (using deb-gview_0.2.8ubuntu3_amd64.deb) ...
Unpacking replacement deb-gview ...
Preparing to replace dpkg-dev 1.16.1.2ubuntu7 (using dpkg-dev_1.16.1.2ubuntu7_all.deb) ...
Unpacking replacement dpkg-dev ...
Preparing to replace g++ 4:4.6.3-1ubuntu5 (using g++_4.6.3-1ubuntu5_amd64.deb) ...
Unpacking replacement g++ ...
Preparing to replace gcc 4:4.6.3-1ubuntu5 (using gcc_4.6.3-1ubuntu5_amd64.deb) ...
Removing old gcc doc directory.
Unpacking replacement gcc ...
Preparing to replace libc6-dev 2.15-0ubuntu10.2 (using libc6-dev_2.15-0ubuntu10.2_amd64.deb) ...
Unpacking replacement libc6-dev ...
Preparing to replace make 3.81-8.1ubuntu1 (using make_3.81-8.1ubuntu1_amd64.deb) ...
Unpacking replacement make ...
Preparing to replace manpages-dev 3.35-0.1ubuntu1 (using manpages-dev_3.35-0.1ubuntu1_all.deb) ...
Unpacking replacement manpages-dev ...
Setting up cpp (4:4.6.3-1ubuntu5) ...
Setting up deb-gview (0.2.8ubuntu3) ...
dpkg: dependency problems prevent configuration of dpkg-dev:
 dpkg-dev depends on libdpkg-perl (= 1.16.1.2ubuntu7); however:
  Package libdpkg-perl is not installed.
dpkg: error processing dpkg-dev (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of g++:
 g++ depends on g++-4.6 (>= 4.6.3-1~); however:
  Package g++-4.6 is not installed.
dpkg: error processing g++ (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.15-0ubuntu10.2); however:
  Version of libc6 on system is 2.15-0ubuntu10.3.
 libc6-dev depends on libc-dev-bin (= 2.15-0ubuntu10.2); however:
  Version of libc-dev-bin on system is 2.15-0ubuntu10.3.
dpkg: error processing libc6-dev (--install):
 dependency problems - leaving unconfigured
Setting up make (3.81-8.1ubuntu1) ...
Setting up manpages-dev (3.35-0.1ubuntu1) ...
dpkg: dependency problems prevent configuration of build-essential:
 build-essential depends on libc6-dev | libc-dev; however:
  Package libc6-dev is not configured yet.
  Package libc-dev is not installed.
  Package libc6-dev which provides libc-dev is not configured yet.
 build-essential depends on g++ (>= 4:4.4.3); however:
  Package g++ is not configured yet.
 build-essential depends on dpkg-dev (>= 1.13.5); however:
  Package dpkg-dev is not configured yet.
dpkg: error processing build-essential (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Setting up gcc (4:4.6.3-1ubuntu5) ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 dpkg-dev
 g++
 libc6-dev
 build-essential
mabz@BELL:~/Desktop$

---

### Post by chili555 on 2013-06-07
> Package g++-4.6 is not installed.
Package libdpkg-perl is not installed.
Package libc-dev is not installed.
libc6-dev depends on libc6 (= 2.15-0ubuntu10.[COLOR="#FF0000"]2[/COLOR]); however:
Version of libc6 on system is 2.15-0ubuntu10.3.
libc6-dev depends on libc-dev-bin (= 2.15-0ubuntu10.[COLOR="#FF0000"]2[/COLOR]); however:
Version of libc-dev-bin on system is 2.15-0ubuntu10.3.Go get them, install them and try again.

OR!!! Install Ubuntu 13.04 where both of these devices are driven by default.

---

### Post by mabz1121 on 2013-06-07
I installed ubuntu 13.04. Everything is working great, thanks.

---

### Post by chili555 on 2013-06-07
> **mabz1121 said:**
> I installed ubuntu 13.04. Everything is working great, thanks.Great news. Glad it's working!

---

### Post by jeeptrash on 2013-06-18
Alright chili, I'm stuck again.  I just updated to version 12.10 and re making this driver does not work for me anymore.  I get no errors and everything builds fine.  I have tried three times with reboots in between.

However this time I am able to get online via USB tethering on my android phone.  Any input on how to resolve the wireless issue.


Your saying that the newer versions support this device, so it should be working shouldn't it? Or do I need to go to version 13.x




Downloading and installing 13.x now, will update if it does not fix the issue.  My Ethernet is working fine also.

---

### Post by chili555 on 2013-06-19
> **jeeptrash said:**
> Downloading and installing 13.x now, will update if it does not fix the issue.  My Ethernet is working fine also.Let us know if it's fixed or if you need help, please.

---

### Post by jeeptrash on 2013-06-19
Ubuntu 13.x solved all my issue.  Thanks for the help.

---

### Post by chili555 on 2013-06-19
> **jeeptrash said:**
> Ubuntu 13.x solved all my issue.  Thanks for the help.Awesome. Thanks for your report because it will help some searchers.

---

### Post by JohnLingad on 2013-07-07
Is these steps ok with BackTrack 5? since its Ubuntu -based?

---

### Post by chili555 on 2013-07-07
> **JohnLingad said:**
> Is these steps ok with BackTrack 5? since its Ubuntu -based?Which kernel version are you running?```
uname -a
```

---

### Post by masoud-rahman on 2013-09-29
Thanks a ton, chili555. Your instructions worked like a breeze and I am now able to connect my laptop through ethernet after 1 year of purchasing it.

Thanks,
Masoud A R

---

### Post by sanhing on 2013-09-29
Original poster here. I just want to again say thanks to chili555 for all his help. Thanks to his expertise and patience, he was able to transform my misery into serenity. I am also delighted to see chilli555's solution has helped so many others. Best wishes to you, one and all.

sanhing

---

### Post by chili555 on 2013-09-29
Thank you both for your very kind words. That's the wonderful nature of the forum. One post helps many. 

I am very grateful for your kindness.

---

