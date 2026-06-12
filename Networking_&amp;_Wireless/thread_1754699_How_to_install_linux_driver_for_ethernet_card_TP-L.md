---
title: "How to install linux driver for ethernet card TP-LINK TF-3239DL"
date: 2011-05-10
forum: Networking &amp; Wireless
---

### Post by regsim on 2011-05-10
Hi, 
I have a dual boot on my computer - with ubuntu 9.04 jaunty jackalope on one side of the partition, and windows 2000 on the other. 

I recently bought - and had installed - a new ethernet card: 
TP-LINK network adapter TF-3239DL. It works perfectly on windows, but not on linux. I understand that the problem is that I need to install the linux driver, which I have available (comes in the CD), but I don't really understand how I am supposed to proceed. The instructions are very unclear to me, and I have relatively little experience.

Thanks for any help ! 
Simona

---

### Post by chili555 on 2011-05-10
I believe your card uses the driver 8139too that's already built in to the kernel. Please open a terminal and run and post:```
sudo modprobe 8139too
dmesg | grep 8139
ifconfig
```Some of the commands may produce no output; sometimes silence speaks volumes. The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by regsim on 2011-05-10
> **chili555 said:**
> I believe your card uses the driver 8139too that's already built in to the kernel. Please open a terminal and run and post:```
sudo modprobe 8139too
dmesg | grep 8139
ifconfig
```Some of the commands may produce no output; sometimes silence speaks volumes. The pipe symbol | is on the right side of my US keyboard on the same key with \.
Thank you for the suggestion. You are right about 8139too. The readme file that came with the card says "this driver was originally based on 8139too.c version 0.9.15.   It has been enhanced to support RTL8139C+ PCI ethernet controller." ... 


The problem is not yet solved, however. Below is the output I got - 
best, 
Simona


simona@ubuntuone:~$ sudo modprobe 8139too
[sudo] password for simona: 
simona@ubuntuone:~$ dmesg | grep 8139
[    0.881390] pci 0000:00:1f.4: reg 20 io port: [0xd400-0xd41f]
[    0.888139] libata version 3.00 loaded.
[    3.803250] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.803318] 8139cp 0000:02:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    3.809742] 8139too Fast Ethernet driver 0.9.28
[    3.809852] 8139too 0000:02:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.811602] eth0: RealTek RTL8139 at 0xac00, 74:ea:3a:84:b7:b9, IRQ 17
[    3.811609] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
simona@ubuntuone:~$ ifconfig
eth2      Link encap:Ethernet  HWaddr 74:ea:3a:84:b7:b9  
          inet6 addr: fe80::76ea:3aff:fe84:b7b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:746 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60502 (60.5 KB)  TX bytes:1188 (1.1 KB)
          Interrupt:17 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2784 (2.7 KB)  TX bytes:2784 (2.7 KB)

simona@ubuntuone:~$

---

### Post by chili555 on 2011-05-10
> [ [COLOR="Red"]3.809742[/COLOR]] 8139too Fast Ethernet driver 0.9.28
[ 3.809852] 8139too 0000:02:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 3.811602] eth0: RealTek RTL8139 at 0xac00, 74:ea:3a:84:b7:b9, IRQ 17
[ 3.811609] eth0: Identified 8139 chip type 'RTL-8100B/8139D'This timestamp indicates that the driver was loaded and associated with the hardware very early in the boot process.> eth2 Link encap:Ethernet HWaddr 74:ea:3a:84:b7:b9
inet6 addr: fe80::76ea:3aff:fe84:b7b9/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:746 errors:0 dropped:0 overruns:0 frame:0
TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:60502 (60.5 KB) TX bytes:1188 (1.1 KB)
Interrupt:17 Base address:0xac00 Hmmmm. Now the interface is eth2??? It was eth0 in dmesg. Does Network Manager see it? Does it try to connect? Any interesting messages here?```
dmesg | grep eth
```

---

### Post by regsim on 2011-05-10
> **chili555 said:**
> This timestamp indicates that the driver was loaded and associated with the hardware very early in the boot process.Hmmmm. Now the interface is eth2??? It was eth0 in dmesg. Does Network Manager see it? Does it try to connect? Any interesting messages here?```
dmesg | grep eth
```

Ok, here is the output this time -- 

simona@ubuntuone:~$ dmesg | grep eth
[    2.569988] Driver 'sd' needs updating - please use bus_type methods
[    2.570011] Driver 'sr' needs updating - please use bus_type methods
[    3.811602] eth0: RealTek RTL8139 at 0xac00, 74:ea:3a:84:b7:b9, IRQ 17
[    3.811609] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   12.718960] udev: renamed network interface eth0 to eth2
[   27.536068] eth2: link up, 100Mbps, full-duplex, lpa 0x45E1
[   37.892028] eth2: no IPv6 routers present
simona@ubuntuone:~$

---

### Post by chili555 on 2011-05-10
> eth2: link up, 100Mbps, full-duplex, lpa 0x45E1This looks like it connected. No? What does Network Manager do in all this? What does this tell us?```
sudo ethtool eth2
```We are looking for the link status.

---

### Post by regsim on 2011-05-10
> **chili555 said:**
> This looks like it connected. No? What does Network Manager do in all this? What does this tell us?```
sudo ethtool eth2
```We are looking for the link status.

it looks like the new ethernet card I bought is called eth2 and that a device called eth0 does not exist (see below). in addition, as you said, eth2 really does looks connected. Except  it does not connect me to the internet...  


simona@ubuntuone:~$ sudo ethtool eth2
[sudo] password for simona: 
Settings for eth2:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 32
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: d
    Current message level: 0x00000007 (7)
    Link detected: yes
simona@ubuntuone:~$ sudo ethtool eth0
[sudo] password for simona: 
Settings for eth0:
Cannot get device settings: No such device
Cannot get wake-on-lan settings: No such device
Cannot get message level: No such device
Cannot get link status: No such device
No data available

---

### Post by chili555 on 2011-05-10
Again, where is Network Manager in all this? When you click the icon, does it show a Wired Network available? If you click Disconnect on the Wireless connection, does wired activate?

---

### Post by regsim on 2011-05-11
> **chili555 said:**
> Again, where is Network Manager in all this? When you click the icon, does it show a Wired Network available? If you click Disconnect on the Wireless connection, does wired activate?

I will try to clarify the situation as best I can:

My computer is very old, and does not have wireless. It is connected to a modem/router which also serves two other computers in the house that do have wireless. 

My Network Manager has two connections:
one is under the tab DSL and that is the connection that bears the name of my internet provider, with the username and password of my internet connection.
the other is under the tab WIRED and bears the name Auto eth0. This must be for internal networks. It has never been used.

the other tabs - WIRELESS, MOBILE BROADBAND and VPN are all empty. 

Until a week ago - before my USB modem broke forcing me to buy a new (ethernet) modem/router and a new ethernet card (I had a faulty ethernet card which I never used because I had a USB modem) - the computer used to connect automatically through the connection under the  DSL  tab. Now it requires that i click on that connection on a drop-down menu and then tries to connect but without success. The words "Wired Connection" also appear on that drop-down menu, but they are grey and not clickable.

thanks again for your efforts, 
Simona

---

### Post by regsim on 2011-05-14
Are you still there? Can anyone help?
Thanks!
Simona

---

