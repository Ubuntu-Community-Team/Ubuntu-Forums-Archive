---
title: "DWL-AG530 IPv4"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by omax on 2009-02-18
Hi guys. I'm having some troubles setting up my D-link DWL-AG530 AR5413 wireless NIC.

I already have a RaLink network-card that works, but I want a second one to route some traffic through that one.

The D-link card shows up in network manager, but no AP's are available.

```
Linux balder 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux
```
```
$ ifconfig ath0
ath0      Link encap:Ethernet  HWaddr 00:13:xx:xx:xx:xx  
          inet6 addr: fe80::213:46ff:fe9b:311f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```
$ iwconfig ath0
ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
$ sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: AR5413 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: wifi0
       version: 01
       serial: 00:13:xx:xx:xx:xx
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

```

```
$ dmesg | grep ath
[    9.507174] ath_hal: module license 'Proprietary' taints kernel.
[    9.508605] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[    9.757265] ath_pci: 0.9.4
[    9.757640] ath_pci 0000:01:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   10.654047] ath_rate_sample: 1.2 (0.9.4)
[  510.696033] ath0: no IPv6 routers present
[ 2691.296019] ath0: no IPv6 routers present

```

As seen above, it tries to use IPv6. I've blacklisted IPv6 in modprobe, but havn't rebooted my computer yet. Would that solve it?

Also, if I solve this - is it possible to route different programs to different NIC's? Such as firefox for ath0 and rtorrent to wlan0

Also, is network bonding available for wifi? (ifenslave)

Regards,
omax

---

### Post by omax on 2009-02-19
I might add that in network manager, the device says "Device is unmanaged"

What does this imply, how do I fix this?

This is my result from 'nm-tool'
```
- Device: ath0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath_pci
  State:             unmanaged
  Default:           no
  HW Address:        00:00:00:00:00:00

  Capabilities:
    Supported:       yes

  Wireless Settings
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points

```

---

