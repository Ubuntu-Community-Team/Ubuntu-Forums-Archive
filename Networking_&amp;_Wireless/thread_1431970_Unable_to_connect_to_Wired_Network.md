---
title: "Unable to connect to Wired Network"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by saurabhgeo on 2010-03-17
I have just installed Kubuntu 9.10 

Earler I was using Ubuntu 9.04 For some reason I am not able to connect to wired network 

Any suggestions ??

---

### Post by chili555 on 2010-03-17
Has a driver attached and created an interface? Please open a terminal and post:```
sudo lshw -C network
ifconfig 
sudo ethtool eth0
```Thanks.

---

### Post by saurabhgeo on 2010-03-17
@chili555 

thanks for reply 

let me tell you what I have tried till now 

All problems started with this 

[http://ubuntuforums.org/showthread.php?t=1431176](http://ubuntuforums.org/showthread.php?t=1431176) my previous thread .

Realising that i cannot make it correct i decidee to reinstall 

and then I reinstalled kubuntu .The internet did not worked both the wired and wireless 

i thought that i am doing some mistake so reinstalled Kubuntu again since i was not sure of the manual partition where one has to choose tpe of file system i choosed ext4 ...

Now in all this mess i have deleted my windows partition :( while reinstalling kubuntu second time  ,which was working fine even when kubuntu was not working . 

The output of the command that you asked me is here below 

ethtool eth0

Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pg
	Wake-on: d
	Current message level: 0x000000ff (255)
	Link detected: yes


ifconfig 

eth0      Link encap:Ethernet  HWaddr 00:21:9b:d7:48:86  
          inet6 addr: fe80::221:9bff:fed7:4886/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1235 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:154563 (154.5 KB)  TX bytes:3546 (3.5 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1640 (1.6 KB)  TX bytes:1640 (1.6 KB)

lshw -C network 

 *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:d7:48:86
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:fe8fc000-fe8fffff ioport:de00(size=256)
  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe7fc000-fe7fffff


please give me suggestion now i am almost mad i am ubuntu user for more than 1.5 years and now i am feeling so weird whats all is happening ...

---

### Post by chili555 on 2010-03-17
Let's see what's happening, or not, under the hood. Please hook up the ethernet cable and post:```
dmesg | grep -e eth -e sky
```Thanks.

---

### Post by saurabhgeo on 2010-03-18
here is the output of the command you asked for 

thanks for you cooperation 

[    0.988830] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.593212] sky2 eth0: addr 00:21:9b:d7:48:86
[    5.368314] input: Dell WMI hotkeys as /devices/virtual/input/input9
[    9.956470] sky2 eth0: enabling interface
[    9.956634] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.197541] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   12.197742] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   22.244035] eth0: no IPv6 routers present

---

### Post by chili555 on 2010-03-18
> [ 12.197541] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[ 12.197742] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 22.244035] eth0: no IPv6 routers presentThis looks like the card was working and connected! Let's try to coax it a bit. Please open a terminal and do:```
sudo ifconfig eth0 down
sudo rmmod -f sky2
sudo modprobe sky2 disable_msi=1
sudo ifconfig eth0 up
```Does it connect? If so, we can make this permanent.

---

### Post by saurabhgeo on 2010-03-18
when i typed the third command a notification appeared in panel right down saying Network Management attached ...

but it does not connect to internet still ... Should I reboot the system to bring about these changes .

Best Regards

---

### Post by saurabhgeo on 2010-03-18
well i also rebooted but no connection still

---

### Post by chili555 on 2010-03-18
Let's create a file:```
sudo gedit /etc/modprobe.d/sky2.conf
```Substitute nano or kate or vim if you do not have gedit. Add two lines:```
alias eth0 sky2
options sky2 disable_msi=1
```Proofread, save and close gedit. Reboot. Can you now connect?

---

### Post by saurabhgeo on 2010-03-18
I was just going to try your last suggestion . And hence booted notebook

And guess what :)

The network is working without implementing last suggestion .

Dude I must thank you for your patience continuing with my post .

Best Regards

---

### Post by saurabhgeo on 2010-03-18
But still I need your help :)

As i told you while messing around I inadvertently deleted dual boot setup for Microsoft Windows .... 

Well any ways i am not a fan of Windows and now would like to remove it all the way completely ... 

But i also see that while installing kubuntu I manually did partitioning and left some portion of hard drive thinking that was for Windows ...  

So Where am i now ? 

Could you tell how to have a  look into my hard disk and also needs your guidance to make the whole disk for Kubuntu ...

But in my mind I also wish to install a Virtual PC for Windows but i guess that is something different than having a dual boot machine .

So please guide me How to proceed since I am bit scared this time to mess up myself again ;)

---

### Post by saurabhgeo on 2010-03-18
But still I need your help 
 
 As i told you while messing around I inadvertently deleted dual boot setup for Microsoft Windows .... 
 
 Well any ways i am not a fan of Windows and now would like to remove it all the way completely ... 
 
 But i also see that while installing kubuntu I manually did partitioning and left some portion of hard drive thinking that was for Windows ... 
 
 So Where am i now ? 
 
 Could you tell how to have a look into my hard disk and also needs your guidance to make the whole disk for Kubuntu ...
 
 But in my mind I also wish to install a Virtual PC for Windows but i guess that is something different than having a dual boot machine .
 
 So please guide me How to proceed since I am bit scared this time to mess up myself again

---

### Post by chili555 on 2010-03-18
This is a question for General Help. Generally, the process is to run fdisk to identify which partition is which with the P command (print, don't change). Then, you should see Linux filesystems, swap and, I assume, NTFS or some such that is easily identifiable as Windows. Make note of the partition you want to delete, /dev/[COLOR="Red"]sda5[/COLOR], for example.

Then use a live CD and Gparted to delete the partition you want to omit and stretch another to fill the empty space. They need to be adjacent if I remember correctly.

Unless you love chaos and disaster, never fool with partitioning on a mounted, running partition.

The geeks over on General Help can fill in the blanks.

---

