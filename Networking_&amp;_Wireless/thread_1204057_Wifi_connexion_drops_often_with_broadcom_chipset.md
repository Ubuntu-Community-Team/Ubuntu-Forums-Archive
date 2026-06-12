---
title: "Wifi connexion drops often with broadcom chipset"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by peyu on 2009-07-04
Hi,

I have a HP Tx2625 tablet pc, and I'm using ubuntu intrepid.
The wifi chipset is Broadcom BCM4322, and I'm not using the restricted driver.

When I am connected to internet through wifi, connection drops often (this morning it drops 3 times in 15 min), which is quite annoying. It reconnects automatically after 15s.
I googled about the error message but I haven't found anything, so may be here somebody can help me.
I'm not far from the wifi router (connexion level is almost 100%), and with another laptop under intrepid connexion never drops (both laptops are in the same desk).

Here is the dmesg output after connection drops:

```

[   87.448979] CPU0 attaching NULL sched-domain.
[   87.448995] CPU1 attaching NULL sched-domain.
[   87.452585] CPU0 attaching sched-domain:
[   87.452591]  domain 0: span 0-1 level MC
[   87.452594]   groups: 0 1
[   87.452600]   domain 1: span 0-1 level CPU
[   87.452602]    groups: 0-1
[   87.452607] CPU1 attaching sched-domain:
[   87.452609]  domain 0: span 0-1 level MC
[   87.452612]   groups: 1 0
[   87.452615]   domain 1: span 0-1 level CPU
[   87.452617]    groups: 0-1
[  154.201994] eth1: Michael MIC verification failed for MSDU from 00:1e:4c:b8:e2:5d keyidx=0
[  154.202037] key[0] alg=TKIP key_set=1 tx_pn=00000000019a rx_pn=000000000173 replays=0 icv_errors=0 local_mic_failures=1
[  154.202042] : TKIP stats from module: Ucast
[  154.277325] eth1: Michael MIC verification failed for MSDU from 00:1e:4c:b8:e2:5d keyidx=0
[  154.277365] key[0] alg=TKIP key_set=1 tx_pn=00000000019e rx_pn=00000000017c replays=0 icv_errors=0 local_mic_failures=2
[  154.277369] : TKIP stats from module: Ucast

```

Lsusb output:

```

Bus 007 Device 003: ID 056a:0093 Wacom Co., Ltd 
Bus 007 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 04f2:b103 Chicony Electronics Co., Ltd 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Lspci output:
```

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
08:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```

Thanks for your help !

---

### Post by peyu on 2009-07-11
anybody knows ?

---

### Post by lessfield on 2009-08-08
i don't think that this N chipset is being developed via linux wireless. Also Broadcom is really slow w/ the linux support.
I'm thinking of removing this chip from my laptop until development picks up

---

### Post by lessfield on 2009-08-08
i don't think that this N chipset is being developed via linux wireless. Also Broadcom is really slow w/ the linux support.
I'm thinking of removing this chip from my laptop until development picks up.

---

### Post by peyu on 2010-01-15
I'm posting again because I'm using now ubuntu karmic and I still have these problems. I'm using the Broadcom 802.11 Linux STA wireless driver for use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware provided by ubuntu.

Nobody knows ?

---

### Post by bkratz on 2010-01-15
You might try looking into this

[http://ubuntuforums.org/showthread.php?t=1055078&highlight=BCM4318](http://ubuntuforums.org/showthread.php?t=1055078&highlight=BCM4318)

Apparently a lot of people are having success

---

### Post by themadhatter0 on 2011-02-02
I had a similar problem, but the connection was only dropped when I was using battery power (it worked fine when connected to the mains). It turns out that the problem was with power management - try running
```
sudo iwconfig eth1 power off
```
when you're running on batter power. Iwconfig should now show that power management is off:
```

$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wwan0     no wireless extensions.

eth1      IEEE 802.11abgn  ESSID:"O2wireless633324"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:26:44:49:62:67   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=5/5  Signal level=-49 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:7  Rx invalid frag:0
          Tx excessive retries:768  Invalid misc:0   Missed beacon:0

```

Check out this thread for info on how to make a script that will turn off power management automatically every time you go to batter power: [http://ubuntuforums.org/showthread.php?t=1597874](http://ubuntuforums.org/showthread.php?t=1597874)

Cheers,
Scott

---

