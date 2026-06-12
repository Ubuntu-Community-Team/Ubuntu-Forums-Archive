---
title: "Atheros AR5BXB63 stopped working"
date: 2009-08-25
forum: Networking &amp; Wireless
---

### Post by lallha on 2009-08-25
Hi, 
I just bought a new Compaq laptop CQ60Z about a month ago, and the wireless card suddenly stop working. It was previously working just fine with a fresh installation of 9.04 as a dual boot with vista basic on the side.  Wired connections still work, but I can't figure out why I can't use the wireless.

What can I do to fix it?

The wireless card is an Atheros AR5BXB63

---

### Post by nasleeps on 2009-08-26
I have a Lenovo Thinkpad R61i with Jaunty 9.04 and I'm seeing this same issue.
It's just died one day about a month ago and I've tried just about everything
I could find on the forums and it still isn't working.

Here's the status right now...I can supply what I've tried upon request.
The madwifi driver is enabled at the moment, it was using ath5k when it died.

Thanks :)

```

$ sudo lspci -vnn
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5212 802.11abg NIC [168c:1014] (rev 01)
        Subsystem: IBM ThinkPad 11a/b/g Wireless LAN Mini Express Adapter (AR5BXB6) [1014:058a]
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f7f00000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint, MSI 00
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [140] Virtual Channel <?>
        Kernel driver in use: ath_pci
        Kernel modules: ath5k, ath_pci

$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
pan0      no wireless extensions.
wifi0     no wireless extensions.
ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:1f:3a:66:db:25  
          inet6 addr: fe80::21f:3aff:fe66:db25/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-1F-3A-66-DB-25-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:0 (0.0 B)  TX bytes:5278 (5.2 KB)
          Interrupt:17 

$ lsmod | grep ath
ath_rate_sample        20608  1 
ath_pci               215352  0 
wlan                  240752  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               371616  3 ath_rate_sample,ath_pci

$ dmesg | grep -P '(A|a)th'
[   10.247374] ath_pci 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.247393] ath_pci 0000:03:00.0: setting latency timer to 64
[   10.797304] MadWifi: ath_attach: Switching rfkill capability off.
[   10.831413] wifi0: Atheros AR5424 chip found (MAC 10.3, PHY SChip 6.1, Radio 10.2)
[   10.920147] ath_pci: wifi0: Atheros 5212: mem=0xf7f00000, irq=17
[   26.940073] ath0: no IPv6 routers present

$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:1f:3a:66:db:25
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:37:23:a8:e2
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full ip=192.168.2.100 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1a:f7:15:3f:15:1d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

$ iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wifi0     Interface doesn't support scanning.
ath0      No scan results
pan0      Interface doesn't support scanning.

$ lsb_release -d
Description:    Ubuntu 9.04

$ uname -mr
2.6.28-15-generic i686

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                               [ OK ]

```

---

### Post by iBurger on 2009-08-26
Quick fix; Reinstall ubuntu and disable all updates except for essential security updates.

My wifi card still works. Please reply if this works for you.

---

### Post by nasleeps on 2009-08-26
This hardly seems to be a 'quick fix', but I suppose I can try it later this week.

Has anyone had success with the newer (.31) kernels, ath5k and an AR5212 chipset?

---

### Post by lallha on 2009-08-26
No need to reinstall.  I don't know how, but rebooting into an older kernel and back into the new one seems to have reset something on the wireless card and fixed it.

---

### Post by nasleeps on 2009-08-26
Which kernel did you boot back to? Which kernel are you on now? Do you have the linux-modules-backports-jaunty package installed?

I've tried going back to previous kernels, but that didn't seem to work for me.

Thanks

---

### Post by iBurger on 2009-08-27
Linux 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009

> works fine.

---

