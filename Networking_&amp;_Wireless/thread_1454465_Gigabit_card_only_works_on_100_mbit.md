---
title: "Gigabit card only works on 100 mbit"
date: 2010-04-14
forum: Networking &amp; Wireless
---

### Post by Ossipon on 2010-04-14
Hello,

I have bought two Asus NX1101 gigabit cards for my kubuntu box and ubuntu server box. The cards are automatically detected as eth1. However the speed is set to 100mbit instead of 1gbit.

ifconfig eth1
```
eth1      Link encap:Ethernet  HWaddr 00:22:15:10:ec:71  
          inet addr:130.89.169.33  Bcast:130.89.175.255  Mask:255.255.240.0
          inet6 addr: fe80::222:15ff:fe10:ec71/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:365778 errors:7 dropped:0 overruns:0 frame:7
          TX packets:3250 errors:1 dropped:0 overruns:1 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32582008 (32.5 MB)  TX bytes:700153 (700.1 KB)
          Interrupt:17
```ethtool eth1
```
Settings for eth1:
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
        PHYAD: 24
        Transceiver: internal
        Auto-negotiation: on

```lshw
```
        *-network:0
             description: Ethernet interface
             product: IP1000 Family Gigabit Ethernet
             vendor: Sundance Technology Inc / IC Plus Corp
             physical id: c
             bus info: pci@0000:00:0c.0
             logical name: eth1
             version: 41
             serial: 00:22:15:10:ec:71
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=Sundance Technology IPG Triple-Speed Ethernet duplex=full ip=130.89.169.33 latency=64 maxlatency=10 mingnt=80 multicast=yes port=MII speed=100MB/s
             resources: irq:17 ioport:ec00(size=256) memory:f7d00000-f7d000ff memory:f7c00000-f7c0ffff(prefetchable)
```I noticed that both lshw and ethtool claim that the card does not support 1000mbit. So changing the speed manually with ethtool doesn't work. In windows XP the card works as it should.

---

### Post by Activist on 2010-05-05
i also have the nx1101 and mine is also recognised as 100mbps...

the problem i have is that at times i have no internet, and if from the network manager i disable networking and enable it again i am online again...

from a little search i did i think it might be because the card is not running full speed...
but how to fix this? :/

---

### Post by SpyrosB on 2010-05-21
Same problem here on Ubuntu 10.4, tried to install the ASUS driver for linux with no luck

[ftp://ftp.asus.com/pub/ASUS/Networking/Adaptor/NX1101/NX1101_Driver_MultiOS.zip](ftp://ftp.asus.com/pub/ASUS/Networking/Adaptor/NX1101/NX1101_Driver_MultiOS.zip)

ReadMe

> b. for kernel 2.6.x

        -------------------

            #make all  => generate ipg.ko

           #insmod ./ipg.ko

           #ifconfig eth0 xxx.xxx.xxx.xxx netmask yyy.yyy.yyy.yyy

              eth0 is your network adapter,use "dmesg" to check it, ex:  eth0, eth1...

              xxx  is your ip address, ex:  192.168.102.211

              yyy  is your netmask address,  ex:255.255.255.0 but i'm getting errors

> root@Akropolis:~/asus# make all
make -C  /lib/modules/2.6.32-22-generic/build SUBDIRS=/root/asus modules 
make[1]:  Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC  [M]  /root/asus/ipg_main.o
In file included from  /root/asus/ipg_main.c:159:
/root/asus/ipg.h:101:26: error:  linux/config.h: No such file or directory
In file included from  /root/asus/ipg_main.c:159:
/root/asus/ipg.h:130: error: &#8216;UTS_RELEASE&#8217;  undeclared here (not in a function)
/root/asus/ipg_main.c: In  function &#8216;ipg_config_autoneg&#8217;:
/root/asus/ipg_main.c:1185: error:  &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/root/asus/ipg_main.c:  In function &#8216;ipg_nic_txcleanup&#8217;:
/root/asus/ipg_main.c:1673: error:  &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/root/asus/ipg_main.c:  In function &#8216;ipg_nic_txfree&#8217;:
/root/asus/ipg_main.c:1775: error:  &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/root/asus/ipg_main.c:  In function &#8216;ipg_nic_open&#8217;:
/root/asus/ipg_main.c:1842: error:  &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/root/asus/ipg_main.c:1960:  error: &#8216;SA_SHIRQ&#8217; undeclared (first use in this function)
/root/asus/ipg_main.c:1960:  error: (Each undeclared identifier is reported only once
/root/asus/ipg_main.c:1960:  error: for each function it appears in.)
/root/asus/ipg_main.c:1962:  warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer  type
include/linux/interrupt.h:117: note: expected &#8216;irq_handler_t&#8217;  but argument is of type &#8216;enum irqreturn_t (*)(int,  void *, struct  pt_regs *)&#8217;
/root/asus/ipg_main.c:1962: warning: passing argument 3  of &#8216;request_irq&#8217; makes integer from pointer without a cast
include/linux/interrupt.h:117:  note: expected &#8216;long unsigned int&#8217; but argument is of type &#8216;char *&#8217;
/root/asus/ipg_main.c:  In function &#8216;init_rfdlist&#8217;:
/root/asus/ipg_main.c:2119: error:  &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/root/asus/ipg_main.c:  In function &#8216;init_tfdlist&#8217;:
/root/asus/ipg_main.c:2207: error:  &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/root/asus/ipg_main.c:  In function &#8216;ipg_get_rxbuff&#8217;:
/root/asus/ipg_main.c:2265: error:  &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/root/asus/ipg_main.c:  In function &#8216;ipg_nic_stop&#8217;:
/root/asus/ipg_main.c:2326: error:  &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/root/asus/ipg_main.c:  In function &#8216;ipg_nic_hard_start_xmit&#8217;:
/root/asus/ipg_main.c:2450:  error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/root/asus/ipg_main.c:  In function &#8216;ipg_nic_rx&#8217;:
/root/asus/ipg_main.c:2946: error: &#8216;struct  net_device&#8217; has no member named &#8216;priv&#8217;
/root/asus/ipg_main.c: In  function &#8216;ipg_nic_rxrestore&#8217;:
/root/asus/ipg_main.c:3203: error:  &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/root/asus/ipg_main.c:  In function &#8216;ipg_nic_get_stats&#8217;:
/root/asus/ipg_main.c:3247: error:  &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/root/asus/ipg_main.c:  In function &#8216;ipg_nic_init&#8217;:
/root/asus/ipg_main.c:3499: error:  &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/root/asus/ipg_main.c:3499:  warning: statement with no effect
/root/asus/ipg_main.c:3508: error:  &#8216;struct net_device&#8217; has no member named &#8216;open&#8217;
/root/asus/ipg_main.c:3508:  warning: statement with no effect
/root/asus/ipg_main.c:3509: error:  &#8216;struct net_device&#8217; has no member named &#8216;stop&#8217;
/root/asus/ipg_main.c:3509:  warning: statement with no effect
/root/asus/ipg_main.c:3510: error:  &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/root/asus/ipg_main.c:3510:  warning: statement with no effect
/root/asus/ipg_main.c:3511: error:  &#8216;struct net_device&#8217; has no member named &#8216;get_stats&#8217;
/root/asus/ipg_main.c:3511:  warning: statement with no effect
/root/asus/ipg_main.c:3512: error:  &#8216;struct net_device&#8217; has no member named &#8216;set_multicast_list&#8217;
/root/asus/ipg_main.c:3513:  warning: statement with no effect
/root/asus/ipg_main.c:3514: error:  &#8216;struct net_device&#8217; has no member named &#8216;do_ioctl&#8217;
/root/asus/ipg_main.c:3514:  warning: statement with no effect
/root/asus/ipg_main.c:3521: error:  &#8216;struct net_device&#8217; has no member named &#8216;change_mtu&#8217;
/root/asus/ipg_main.c:3521:  warning: statement with no effect
/root/asus/ipg_main.c: In function  &#8216;ipg_nic_do_ioctl&#8217;:
/root/asus/ipg_main.c:3567: error: &#8216;struct  net_device&#8217; has no member named &#8216;priv&#8217;
/root/asus/ipg_main.c: In  function &#8216;ipg_pciremove_linux2_4&#8217;:
/root/asus/ipg_main.c:3843: error:  &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/root/asus/ipg_main.c:3893:  error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/root/asus/ipg_main.c:  In function &#8216;ipg_pciprobe_linux2_4&#8217;:
/root/asus/ipg_main.c:4000:  error: implicit declaration of function &#8216;SET_MODULE_OWNER&#8217;
/root/asus/ipg_main.c:4011:  error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/root/asus/ipg_main.c:  In function &#8216;init_module&#8217;:
/root/asus/ipg_main.c:4045: error:  implicit declaration of function &#8216;pci_module_init&#8217;
/root/asus/ipg_main.c:  In function &#8216;Set_LED_Mode&#8217;:
/root/asus/ipg_main.c:4250: error:  &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/root/asus/ipg_main.c:  In function &#8216;Set_PHYSet&#8217;:
/root/asus/ipg_main.c:4279: error: &#8216;struct  net_device&#8217; has no member named &#8216;priv&#8217;
make[2]: ***  [/root/asus/ipg_main.o] Error 1
make[1]: *** [_module_/root/asus]  Error 2
make[1]: Leaving directory  `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [all] Error 2

---

### Post by Rayve on 2010-06-23
Spyros,

I believe this has to do with a problem in the 2.6+ kernel which  the old net_device structure with a new one called net_device_ops, this apparently affects USB Wireless adapters and VBox... I'm doing some research with Google and other posts here to try to fix my USB-N10... will post back if I manage to fix anything.

References: [http://ubuntuforums.org/showthread.php?t=1285828](http://ubuntuforums.org/showthread.php?t=1285828)
[http://www.virtualbox.org/ticket/4264](http://www.virtualbox.org/ticket/4264)

---

### Post by Offshore on 2011-02-13
Still no luck?
Having same problem (cannot build shipped or downloaded drivers / cannot get 1gbps link with available mod ipg -- just 100mbps), Ubuntu Server 10.04.2 LTS.

---

