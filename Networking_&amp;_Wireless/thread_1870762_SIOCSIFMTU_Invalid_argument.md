---
title: "SIOCSIFMTU: Invalid argument"
date: 2011-10-27
forum: Networking &amp; Wireless
---

### Post by atif7865 on 2011-10-27
Hi All,

I am trying to set up a lab in my home. for that i need to have a mtu value of atleast 1546, 
I have a broadcom gigabit NIC BCM5751KFBG PCI Express,but i cant increase the mtu on my machine.
 I have a hp pavillion desktop running ubuntu 11.10.

I also have pci boradcom NIC BCM5782KFB but i still cant change mtu value.  Documents from broadcom indicate that the card is capable of jumbo frames upto 9K.([http://www.broadcom.com/docs/support/ethernet_nic/Broadcom_NetLink-NetXtreme_DTM_306.pdf](http://www.broadcom.com/docs/support/ethernet_nic/Broadcom_NetLink-NetXtreme_DTM_306.pdf))

I try to change the value but issuing followig command:

"sudo ifconfig eth1 mtu 1600" 
and i get the following error:
SIOCSIFMTU: invalid argument

I cant even change it to 1501,

I read somewhere on the web that there is a lock on the jumbo frames configuration so that it doesnt result in system panics.
but i need the jumbo frames and was wondering what can i do to get it to work, below are some info from my system. 
p.s. i am newbie to ubuntu so please help me out.

============================sudo uname -a ================================

Linux atef-NC757AA-ABA-a6757c 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

===============================lsmod==================================
psmouse                73882  0 
serio_raw              13166  0 
edac_core              53746  0 
k10temp                13166  0 
edac_mce_amd           23709  0 
i2c_nforce2            13058  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
8021q                  24173  0 
garp                   14602  1 8021q
stp                    12931  1 garp
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            57901  1 
uas                    18027  0 
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  2 rt73usb,firewire_core
tg3                   147729  0 
sata_nv                32305  2 
forcedeth              67563  0 
pata_amd               14121  0

(note: i dont see any modules relating to network cards, does it mean i dont have drivers for the card at all?

=====================ifconfig==================================
                  

eth0      Link encap:Ethernet  HWaddr 00:24:8c:aa:79:f0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:10:18:24:8e:11  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

rename2   Link encap:Ethernet  HWaddr 00:10:18:0d:14:a0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

wlan0     Link encap:Ethernet  HWaddr 00:22:5f:81:b4:32  
          inet addr:192.168.0.19  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:5fff:fe81:b432/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:882 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:203706 (203.7 KB)  TX bytes:13990 (13.9 KB)

================lspci -vvnn | grep 14e4 (i think 14e4 is for broadcom)=========================

01:0a.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5782 Gigabit Ethernet [14e4:1696] (rev 03)
04:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 21)
    Subsystem: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677]


please let me know if more info is needed

---

### Post by atif7865 on 2011-10-27
any one guys??
help appreciated.

---

### Post by atif7865 on 2011-10-27
strange things happen. my onboard wifi card, indicated as wlan0 above was able to get set up to 2000MTU

i am ready to bang my head against the wall. two gigabit cards with documentation mentioning they are capable of jumbo frames cant do it???

cant get more frustrating.

---

### Post by atif7865 on 2011-10-27
Can there be a lock or something on wired connections so that they cant accept more than 1500 ?
i plugged in a usb wireless and it was able to accept jumbo frames as well.

any clues?

---

### Post by atif7865 on 2011-10-28
Wow, i was expecting some kind of answer by now. this shouldnt be this hard

---

### Post by darknuts on 2013-02-24
Did you ever figure it out? I have the same problem.

---

### Post by UndeadBob on 2013-07-15
> **darknuts said:**
> Did you ever figure it out? I have the same problem.

ditto

---

