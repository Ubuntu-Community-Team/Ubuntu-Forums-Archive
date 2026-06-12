---
title: "ndiswrapper and wpc54gv2 problems"
date: 2006-01-08
forum: Networking &amp; Wireless
---

### Post by cloudedice on 2006-01-08
Early December I installed Ubuntu and got my Linksys WPC54G Version2 wireless card up and running with out any help. Last week it just stopped working. I don't know if I did anything to cause it, but I have since completely reinstalled Ubuntu, just to make sure that I couldn't have screwed anything up and I still can't get it to work again.

I've checked the numerous posts related to ndiswrapper and the wpc54g card on this site and others, but to no avail. I've got the windows drivers installed properly (lstinds) and when that didn't work by itself, I tried including lsbcmnds also, just in case.

Any help is greatly appreciated.

Cloudedice

```

cloudedice@cloudedice:~$ lsmod |grep ndis
ndiswrapper        130824  0
usbcore               118044  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd

```

```

cloudedice@cloudedice:~$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:10 dBm   Sensitivity=0/3
          RTS thr:4096 B   Fragment thr:4096 B
          Power Management:off
          Link Quality:100  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

snipped to possibly relavent information

cloudedice@cloudedice:~$ dmesg
[4294705.681000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4294715.881000] Linux Kernel Card Services
[4294715.881000]   options:  [pci] [cardbus] [pm]
[4294715.899000] PCI: Enabling device 0000:00:0a.0 (0000 -> 0002)
[4294715.899000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
[4294715.899000] Yenta: CardBus bridge found at 0000:00:0a.0 [103c:0850]
[4294715.899000] Yenta O2: res at 0x94/0xD4: 00/ea
[4294715.899000] Yenta O2: enabling read prefetch/write burst
[4294716.019000] Yenta: ISA IRQ mask 0x0018, PCI irq 11
[4294716.019000] Socket status: 30000821
[4294718.393000] ndiswrapper: driver lstinds (Linksys,03/10/2004,6.0.0.18) loaded
[4294718.393000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[4294718.393000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
[4294718.394000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[4294719.077000] ndiswrapper: using irq 11
[4294719.617000] wlan0: ndiswrapper ethernet device 00:0f:66:c6:bb:64 using driver lstinds, configuration file 104C:9066:1737:0033.5.conf
[4294719.618000] wlan0: encryption modes supported: WEP, WPA with TKIP
[4294741.091000] cs: IO port probe 0x100-0x4ff: excluding 0x200-0x207 0x220-0x22f 0x330-0x337 0x388-0x38f
[4294741.094000] cs: IO port probe 0xc00-0xcf7: clean.
[4294741.095000] cs: IO port probe 0xa00-0xaff: clean.
[4294755.176000] IPv6 over IPv4 tunneling driver
[4294829.413000] wlan0: no IPv6 routers present

```

```

cloudedice@cloudedice:~$ ndiswrapper -l
Installed ndis drivers:
lsbcmnds        driver present
lstinds driver present, hardware present

```

---

### Post by LightShear on 2006-01-09
Try "iwlist scanning" in terminal. Post it's output and we'll see if it's finding your router (presuming you have a router it's connecting to).

---

### Post by waldorf on 2006-01-09
Same thing has happened to me. I don't have any suggestions but am interested to see how things go for you.

I know it may not be good form to reply without advice but I figure if people know that there are enough of us with the same problem, maybe it will get more attention.

---

### Post by cloudedice on 2006-01-09
It's able to see the routers in my area, but is not able to access mine.  I've bolded mine. (I had removed any sort of security device except MAC address filtering just for testing purposes. I only keep the wireless feature on long enough to test until I solve the problem.)

```

cloudedice@cloudedice:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Interface doesn't support scanning : Operation not supported

wlan0     Scan completed :
          Cell 01 - Address: 00:13:10:9E:52:FB
                    ESSID:"AlphaConnect"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-66 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
          Cell 02 - Address: 00:13:46:4B:CB:2C
                    ESSID:"Wyoming"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-65 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:11:95:78:45:F2
                    ESSID:"andysnet"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-71 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:14:BF:2B:39:3D
                    ESSID:"linksys_SES_11405"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-74 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    Extra:wpa_ie=dd180050f20101000050f20201000050f20201000050f2020000
          Cell 05 - Address: 00:13:10:74:D7:92
                    ESSID:""
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-70 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    Extra:wpa_ie=dd180050f20101000050f20401000050f20401000050f2020000
          [B]Cell 06 - Address: 00:0F:66:CD:F4:22
                    ESSID:"MurkyWater"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-32 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0[/B]
          Cell 07 - Address: 00:14:BF:38:8A:54
                    ESSID:"nynexman"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-32 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 08 - Address: 00:12:17:33:AC:F3
                    ESSID:"ceptxj"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-81 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 09 - Address: 00:0F:66:E2:B8:FF
                    ESSID:""
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:0/100  Signal level:-85 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

sit0      Interface doesn't support scanning.

```

---

### Post by Lambert on 2006-01-09
Sometimes the scan isn't correct so this may be incorrect but what i see is your router and card using different protocols. 

Notice your output of iwconfig, it says 802.11g
iwlist shows the router in 802.11b

So if the scan was correct then use this command in a terminal to change the card to the b protocol

```
sudo iwpriv wlan0 network_type b
```

---

### Post by cloudedice on 2006-01-09
The router accepts both 802.11b and g, but the speeds listed go all the way up to the 802.11g limit of 54Mb/s

---

### Post by healychan on 2006-01-10
How did you get that card running?? I had that card before but whenever I tried to bring it up, the system hang.

Is your card using Marvell chipset?? As far as I know, most card with Marvell chipset doesn't work well with any Linux distro. Can you post the output of "lspci".

Many people having problems with this model.

---

### Post by cloudedice on 2006-01-10
WPC54G Version 2 has the Texas Instruments chip as far as I know. Version 1 and 3 have two different Broadcom chips. Not sure about Version 4

```

cloudedice@cloudedice:~$ sudo lspci -v
0000:02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
        Subsystem: Linksys: Unknown device 0033
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at d0120000 (32-bit, non-prefetchable) [size=8K]
        Memory at d0100000 (32-bit, non-prefetchable) [size=128K]
        Capabilities: [40] Power Management version 2

```

---

### Post by healychan on 2006-01-10
Surely your card is differ from my one. My card is using Marvell chipset.

---

