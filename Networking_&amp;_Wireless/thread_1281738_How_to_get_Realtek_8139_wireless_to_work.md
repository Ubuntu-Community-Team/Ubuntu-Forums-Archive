---
title: "How to get Realtek 8139 wireless to work"
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by dreamsR4living on 2009-10-03
I have just installed a laptop for someone with xubuntu jaunty 9.04, but I can't seem to get the wireless to work. The laptop uses a Realtek RTL-8139 ethernet card and an Agere Systems Device. I have posted some outputs down below. 

```
nfa@laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS300 Host Bridge [1002:5830] (rev 02)
00:01.0 PCI bridge [0604]: ATI Technologies Inc Radeon 9100 IGP AGP Bridge [1002:5838]
00:13.0 USB Controller [0c03]: ATI Technologies Inc OHCI USB Controller #1 [1002:4347] (rev 01)
00:13.1 USB Controller [0c03]: ATI Technologies Inc OHCI USB Controller #2 [1002:4348] (rev 01)
00:13.2 USB Controller [0c03]: ATI Technologies Inc EHCI USB Controller [1002:4345] (rev 01)
00:14.0 SMBus [0c05]: ATI Technologies Inc SMBus [1002:4353] (rev 18)
00:14.1 IDE interface [0101]: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller [1002:4349]
00:14.3 ISA bridge [0601]: ATI Technologies Inc Device [1002:434c]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller [1002:4342]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP150 AC'97 Audio Controller [1002:4341]
00:14.6 Modem [0703]: ATI Technologies Inc IXP AC'97 Modem [1002:434d] (rev 01)
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP] [1002:5835]
02:04.0 Network controller [0280]: Agere Systems Device [11c1:ab34]
02:0b.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
```

```
nfa@laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.
```

```
nfa@laptop:~$ lsmod | grep 8139
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp
```

```
nfa@laptop:~$ sudo lshw -C network
[sudo] password for nfa: 
  *-network:0 UNCLAIMED   
       description: Network controller
       product: Agere Systems
       vendor: Agere Systems
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 00
       width: 32 bits
       clock: 33MHz
       configuration: latency=0
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:02:0b.0
       logical name: eth0
       version: 10
       serial: 00:0d:5e:1c:63:0b
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 76:f9:14:d2:45:c5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

Does anyone know how to get my wireless to work? Thanks in advance!

---

### Post by chili555 on 2009-10-03
Your Realtek 8139 is both working fine and ***not*** your wireless. You may wish to change the title of your thread to ask for help getting your Agere Systems Device [11c1:ab34] working. I have done some preliminary googling and, so far, I'm stumped.

---

### Post by dreamsR4living on 2009-10-03
> **chili555 said:**
> Your Realtek 8139 is both working fine and ***not*** your wireless. You may wish to Change the title of your thread to ask for help getting your Agere Systems Device [11c1:ab34] working. I have done some preliminary googling and, so far, I'm stumped.

Thanks for the tip chili555, I changed the thread title and going to search for Agere Systems. 

If there is anyone who has experience with this Agere Systems Wireless device, please let me know.

---

