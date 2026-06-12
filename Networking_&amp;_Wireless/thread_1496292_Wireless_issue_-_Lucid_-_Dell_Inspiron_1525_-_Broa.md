---
title: "Wireless issue - Lucid - Dell Inspiron 1525 - Broadcom 4328"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by shawn.abdushakur on 2010-05-29
I've tried using network manager and wicd, no luck. Network manager keeps asking for the passkey and wicd reports a bad passphrase and i'm certain in both cases that the key is correct as it works on my other computers.

Dell Inspiron 1525 with a Broadcom 4328 running Ubuntu Lucid.

lspci:

0b:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)

iwconfig:

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:169
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

ifconfig:

eth1      Link encap:Ethernet  HWaddr 00:22:69:ab:1e:4d  
          inet6 addr: fe80::222:69ff:feab:1e4d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:185
          TX packets:1 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:113 (113.0 B)  TX bytes:143 (143.0 B)
          Interrupt:17 Base address:0xc000 

lsmod (though i'm not sure i've selected the right modules):

wl                   1964968  0 
lib80211                6119  2 lib80211_crypt_tkip,wl

dmesg:

shawn@inpsiron1525:~$ dmesg | grep wl
[   12.178344] wl: module license 'MIXED/Proprietary' taints kernel.
[   12.289149] wl 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.289159] wl 0000:0b:00.0: setting latency timer to 64

dmesg | grep lib80211
[   12.158744] lib80211: common routines for IEEE802.11 drivers
[   12.158749] lib80211_crypt: registered algorithm 'NULL'
[   12.389554] lib80211_crypt: registered algorithm 'TKIP'

shawn@inpsiron1525:~$ sudo lshw -C network
[sudo] password for shawn: 
  *-network
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 03
       serial: 00:22:69:ab:1e:4d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:fe7fc000-fe7fffff memory:f0000000-f00fffff(prefetchable)

shawn@inpsiron1525:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

 lsb_release -d
Description:    Ubuntu 10.04 LTS

shawn@inpsiron1525:~$ uname -mr
2.6.32-22-generic x86_64

shawn@inpsiron1525:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                       Ignoring unknown interface eth0=eth0.

Thanks for any help.

Shawn

---

### Post by shawn.abdushakur on 2010-06-04
bump

---

### Post by clockworkpc on 2010-08-09
Hi,

I'm finding the same problem.

Using Linux Mint 9, and when I boot up wireless is great.
But after a while wireless just drops out and then I can't reconnect to my network unless I reboot.

Logging out doesn't help either.

---

### Post by rwinn on 2010-08-18
bumpity

many, many hours trolling and i believe that the only working solution for us is to install different wifi card

i keep hoping that someone will find a fix for ubuntu

dell 1721
broadcom 4328

thanks :(

---

### Post by Trinity33 on 2010-08-18
> **shawn.abdushakur said:**
> I've tried using network manager and wicd, no luck. Network manager keeps asking for the passkey and wicd reports a bad passphrase and i'm certain in both cases that the key is correct as it works on my other computers.

Dell Inspiron 1525 with a Broadcom 4328 running Ubuntu Lucid.

lspci:

0b:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)

iwconfig:

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:169
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

ifconfig:

eth1      Link encap:Ethernet  HWaddr 00:22:69:ab:1e:4d  
          inet6 addr: fe80::222:69ff:feab:1e4d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:185
          TX packets:1 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:113 (113.0 B)  TX bytes:143 (143.0 B)
          Interrupt:17 Base address:0xc000 

lsmod (though i'm not sure i've selected the right modules):

wl                   1964968  0 
lib80211                6119  2 lib80211_crypt_tkip,wl

dmesg:

shawn@inpsiron1525:~$ dmesg | grep wl
[   12.178344] wl: module license 'MIXED/Proprietary' taints kernel.
[   12.289149] wl 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.289159] wl 0000:0b:00.0: setting latency timer to 64

dmesg | grep lib80211
[   12.158744] lib80211: common routines for IEEE802.11 drivers
[   12.158749] lib80211_crypt: registered algorithm 'NULL'
[   12.389554] lib80211_crypt: registered algorithm 'TKIP'

shawn@inpsiron1525:~$ sudo lshw -C network
[sudo] password for shawn: 
  *-network
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 03
       serial: 00:22:69:ab:1e:4d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:fe7fc000-fe7fffff memory:f0000000-f00fffff(prefetchable)

shawn@inpsiron1525:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

 lsb_release -d
Description:    Ubuntu 10.04 LTS

shawn@inpsiron1525:~$ uname -mr
2.6.32-22-generic x86_64

shawn@inpsiron1525:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                       Ignoring unknown interface eth0=eth0.

Thanks for any help.

Shawn



check up this tread [http://ubuntuforums.org/showthread.php?t=1053167](http://ubuntuforums.org/showthread.php?t=1053167)

---

