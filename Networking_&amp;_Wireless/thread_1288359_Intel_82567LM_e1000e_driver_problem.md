---
title: "Intel 82567LM e1000e driver problem"
date: 2009-10-11
forum: Networking &amp; Wireless
---

### Post by tumtumma on 2009-10-11
[FONT=Verdana]I apologies for my bad English, but i will do my best.
Ubuntu is relative new for me so I hope that you could help me out.

[/FONT]  [FONT=&quot][FONT=Verdana]While installing "Ubuntu[/FONT] 8.04 LTS[/FONT]Server 64 bit" there was no network device found. 
After the installation i tried to install de drivers from the Intel site with their README.txt
see link below:
[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=3003[FONT=&quot]&#9001;[/FONT]=eng]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=3003&lang=eng")

the driver file is located in /home/user/drivers/e1000e-1.0.2.5

/lib/modules/2.6.24-24-server/kernel/drivers/net shows: 
e1000, e1000e, e100.ko,eepro100.ko   and a lot more. 

I have searched the internet and ubuntu forums for a solution but I couldn't find anything useful. 

***I just cant get it working! Please help.***

What do I know:
-I don’t have internet or an ip 
-ifconfig shows only the lo but no eth0
-one light blinks sometimes and the other light is always on, when the cabel is connected
-the output of the following comment is " lspci -v | grep Eth" : [I]00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
[/I]

extra information:[I]
mainbord:     Intel dq45cb[/I][I]
kernel:         2.6.24-24-server[/I]

Thanks!

---

### Post by chili555 on 2009-10-11
How about letting us see:```
sudo cat /var/log/messages | grep e100
sudo cat /var/log/messages | grep -i eeprom
```Thanks.

---

### Post by tumtumma on 2009-10-11
sudo cat /var/log/messages | grep e100
[1353.389696] e1000e: Intel(R) PRO/1000 Network Driver - 0.2.0
[1353.389698] e1000e: Copyright bbla bla...
[2469.906616] e1000e: Intel(R) PRO/1000 Network Driver - 0.2.0
[2469.906619] e1000e: Copyright bbla bla...[FONT=monospace]

[/FONT]sudo cat /var/log/messages | grep -i eeprom 
NONE

I also discovered that when i do 
*cd /home/user/drivers/e1000e01.0.2.5/src *
and do: 
*Sudo make install  *
outcome is:
*sudo: make: command not found*
OR i do this:
*# make install* (Like in README.txt)
the outcome is nothing, so i don't no if anything is happend.

In other forums their saying that something is going to happen like> 
[http://ubuntuforums.org/showthread.php?t=1276211&highlight=e1000e&page=3](http://ubuntuforums.org/showthread.php?t=1276211&highlight=e1000e&page=3)

---

### Post by chili555 on 2009-10-11
> sudo cat /var/log/messages | grep e100
[1353.389696] e1000e: Intel(R) PRO/1000 Network Driver - 0.2.0
[1353.389698] e1000e: Copyright bbla bla...
[2469.906616] e1000e: Intel(R) PRO/1000 Network Driver - 0.2.0
[2469.906619] e1000e: Copyright bbla bla...That seems to indicate that the native kernel module is loading. Before we troubleshoot your compile issue, let's see if we can make the native module work. Please let us see:```
sudo lshw -C network
```We are hoping your ethernet card has a driver and an interface attached.> sudo cat /var/log/messages | grep -i eeprom
NONEIn this case, no news about EEPROM troubles is definately good news!

---

### Post by tumtumma on 2009-10-11
*sudo lshw -C network*

*-network UNCLAIMED
description: Ethernet controller
product: 82567LM-3 Gigabit Network Connection
vendor: Intel Corporation
physical id: 19
bus info: pci@0000:00:19.0
version: 02
width: 32 bits
clock: 33 MHz
capabilities: pm msi bus_master cap_list
configuration: latency=0[FONT=monospace] [/FONT]

---

### Post by chili555 on 2009-10-11
I was interested in reading this: [http://groups.google.com/group/linux.debian.bugs.dist/msg/3c4b86deda584d85?pli=1](http://groups.google.com/group/linux.debian.bugs.dist/msg/3c4b86deda584d85?pli=1)

Especially this:> In Ubuntu support for these ICH10 NICs was added to kernel 2.6.27-6.9: You have an earlier kernel, 2.6.24-24.

One option is to re-install a later version, 9.04, for example. Another option is to try to get the downloaded file compiled. Are you able to connect to the internet, wirelessly, perhaps? Please open System -> Admin -> Synaptic and install, if it's not already there, *build-essential* and *linux-headers-generic*. Each of these will add other packages which you should accept.

I am going a bit by memory here; it has been a while since I worked with 2.6.24-xx.

Then do:```
cd /home/user/drivers/e1000e01.0.2.5/src
make
sudo make install
sudo rmmod -f e1000e
```This gets the old, non-working module unloaded.```
sudo modprobe e1000e
```...and the new one loaded.```
sudo ifconfig eth0 up
```Now can you connect?

---

### Post by tumtumma on 2009-10-11
> i don't have the possibility to connect to the Internet so i can't download: *build-essential* and *linux-headers-generic. *

is it not possible to get *build-essential* and *linux-headers-generic *from the ubuntu cd ?I went toe /etc/apt/sources.list and removed the # from 

```
# deb cdrom:[Ubuntu 8.04_Hardy_Heron - Release i386 (20070419.1)]/ hardy main restricted

```and i did,   sudo apt-get install build-essential (AND IT WORKED)
and, sudo apt-get install linux-headers-server (not generic) (AND THAT TO WORKED)

i am so happy right now XD

then i did your commands and now i have my ETH0 device in my ifconfig !

---

### Post by tumtumma on 2009-10-11
I have my internet now working, thanks for your help chili555! 

I appreciate it very much! :)

---

### Post by chili555 on 2009-10-11
Very happy to help! I am very glad it's working. Now I shall carve another notch in the handle of my old .44.

---

### Post by Qtea on 2010-05-11
I'm relieved to read that it has been proved to be possible to get the wireless run on 82567LM, but I wasn't able to reproduce the trick on my laptop. I downloaded the [kernel module](http://downloadmirror.intel.com/15817/eng/e1000e-1.1.19.tar.gz) from Intel and loaded it as instructed above.

```
tea@kiva:~$ uname -r
2.6.32-21-generic
```

```
tea@kiva:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:24:7e:68:6a:93
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.1.19-NAPI duplex=full firmware=1.8-3 ip=83.150.115.164 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:fc400000-fc41ffff memory:fc425000-fc425fff ioport:1840(size=32)
```


```
tea@kiva:~$ dmesg | grep e1000e
[    1.037543] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[    1.037546] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    1.037593] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.037604] e1000e 0000:00:19.0: setting latency timer to 64
[    1.037723] e1000e 0000:00:19.0: irq 27 for MSI/MSI-X
[   15.832706] e1000e 0000:00:19.0: irq 27 for MSI/MSI-X
[   15.888591] e1000e 0000:00:19.0: irq 27 for MSI/MSI-X
[   32.012892] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1644.808314] e1000e: eth0 NIC Link is Down
[ 1646.473063] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1650.236394] e1000e: eth0 NIC Link is Down
[ 1664.292910] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2250.480350] e1000e 0000:00:19.0: PCI INT A disabled
[ 2264.743761] e1000e: Intel(R) PRO/1000 Network Driver - 1.1.19-NAPI
[ 2264.743764] e1000e: Copyright(c) 1999 - 2010 Intel Corporation.
[ 2264.743806] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 2264.743820] e1000e 0000:00:19.0: setting latency timer to 64
[ 2264.908979] e1000e 0000:00:19.0: irq 27 for MSI/MSI-X
[ 2265.080713] e1000e 0000:00:19.0: irq 27 for MSI/MSI-X
[ 2265.136887] e1000e 0000:00:19.0: irq 27 for MSI/MSI-X
[ 2267.013117] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3624.436401] e1000e: eth0 NIC Link is Down
[ 3633.337109] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4074.932475] e1000e 0000:00:19.0: irq 27 for MSI/MSI-X
[ 4074.988204] e1000e 0000:00:19.0: irq 27 for MSI/MSI-X
[ 4076.552974] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX

```

I seem not to have any issues with NVM checksum like what has been [reported](http://ubuntuforums.org/showthread.php?t=1050970) for 82567LM. What more could I try?

---

### Post by chili555 on 2010-05-11
> *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: [COLOR="Red"]eth0[/COLOR]
       version: 03
       serial: 00:24:7e:68:6a:93
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.1.19-NAPI duplex=full firmware=1.8-3 [COLOR="Red"]ip=83.150.115.164[/COLOR] latency=0 [COLOR="Red"]link=yes [/COLOR]multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:fc400000-fc41ffff memory:fc425000-fc425fff ioport:1840(size=32)I am not sure what your question is, frankly. You have an interface, the link is up and you have an IP address. What is wrong?

---

### Post by Qtea on 2010-05-11
> **chili555 said:**
> I am not sure what your question is, frankly. You have an interface, the link is up and you have an IP address. What is wrong?

Sorry, I didn't make myself very clear. Yes I do have a wired connection, but wireless is still missing.

```
tea@kiva:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

---

### Post by chili555 on 2010-05-11
> I'm relieved to read that it has been proved to be possible to get the wireless run on 82567LMNot true. 

This thread is about how to fix an Intel 82567LM wired ethernet driver. It has nothing to do with wireless. Please start a new thread and tell us this: [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by ColinOpseth on 2010-07-26
I just want to add that I followed these exact instructions to get my NIC working on a new Lenovo server at work. I downloaded the driver from Intel's website and followed the make install procedure. I was online within 2 minutes (after looking for 2 days for a solution)!

Thanks for the help, guys! I appreciate your hard work in never giving up when you find a problem.

---

### Post by ryanfmac on 2011-12-15
I am having the same problem with an Dell Latitude E6500 after having the motherboard replaced.  It appears the e1000e driver is loading since lsmod shows
e1000e                119888  0 
but
lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list
       configuration: latency=0
       resources: memory:f6fe0000-f6ffffff memory:f6fdb000-f6fdbfff ioport:efe0(size=32)

This all looks similar to the earlier postings except for the output of 
dmesg | grep e1000e
[    0.928578] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[    0.928580] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    0.928624] e1000e 0000:00:19.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.928633] e1000e 0000:00:19.0: setting latency timer to 64
[    0.928739] e1000e 0000:00:19.0: irq 29 for MSI/MSI-X
[    1.048968] e1000e 0000:00:19.0: PCI INT A disabled
[    1.048973] e1000e: probe of 0000:00:19.0 failed with error -5

any ideas what this error could be caused by?  After the motherboard swap I'm still having problems with the laptop intermittently turning off immediately after powering on and shutting down when I request a restart so...

additionally:
uname -a
Linux crow 2.6.32-36-generic #79-Ubuntu SMP Tue Nov 8 22:29:26 UTC 2011 i686 GNU/Linux
and
lspci
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
    Subsystem: Dell Device 024f
    Flags: fast devsel, IRQ 22
    Memory at f6fe0000 (32-bit, non-prefetchable) [size=128K]
    Memory at f6fdb000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at efe0 [size=32]
    Capabilities: [c8] Power Management version 2
    Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [e0] PCIe advanced features <?>
    Kernel modules: e1000e

---

