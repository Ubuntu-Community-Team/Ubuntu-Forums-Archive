---
title: "cannot ping the gateway"
date: 2011-02-12
forum: Networking &amp; Wireless
---

### Post by yushengc on 2011-02-12
I ran into a network trouble, I am so confused that:

I can ping my IP, and other PC in the same LAN, but I **CANNOT **ping the gateway on my 10.04LTS ubuntu. 
Other PC in the same LAN(Ubuntu 10.04LTS)  could ping the gateway and my IP. 

I thought that (1)network cable is OK because I could ping the other PC in the same LAN.
(2)Gateway is OK because other PC could ping it. 
(3)setting of operating system might be somehow wrong. 

I have tried to restart the network several times and still not works. I followed the [HOW-To debug tips]("http://www.ruf.rice.edu/%7Erlug/help/net-debug.html#2") and following is the results. Any suggestions?

1. ifconfig
eth2      Link encap:Ethernet  HWaddr 00:1d:7d:aa:d5:d3  
          inet addr:140.112.61.75  Bcast:140.112.61.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:feaa:d5d3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9765 errors:0 dropped:0 overruns:0 frame:0
          TX packets:373 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:911897 (911.8 KB)  TX bytes:50487 (50.4 KB)
          Interrupt:23 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1056 (1.0 KB)  TX bytes:1056 (1.0 KB)

[COLOR=Red]indicating that linux could recognize a network card, eth2[/COLOR]

2. dmesg | grep -3 -i eth
```

[    1.110431] scsi1 : pata_atiixp
[    1.111578] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf900 irq 14
[    1.111582] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf908 irq 15
[    1.116285] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.116306]   alloc irq_desc for 23 on node -1
[    1.116309]   alloc kstat_irqs on node -1
[    1.116320] r8169 0000:02:0f.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.116350] r8169 0000:02:0f.0: no PCI Express capability
[    1.116973] eth0: RTL8169sc/8110sc at 0xf8092000, 00:1d:7d:aa:d5:d3, XID 18000000 IRQ 23
[    1.122043] ahci 0000:00:12.0: version 3.0
[    1.122059]   alloc irq_desc for 22 on node -1
[    1.122061]   alloc kstat_irqs on node -1
--
[    9.131199] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[    9.135161] Linux agpgart interface v0.103
[    9.135435] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[    9.150142] udev: renamed network interface eth0 to eth2
[    9.202428] parport_pc 00:0a: reported by Plug and Play ACPI
[    9.202487] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    9.301263] lp0: using parport0 (interrupt-driven).
--
[    9.615416] vga16fb: mapped to 0xc00a0000
[    9.615422] vga16fb: not registering due to another framebuffer present
[    9.647356] Console: switching to colour frame buffer device 128x48
[    9.801585] r8169: eth2: link up
[   10.508888] CPU0 attaching NULL sched-domain.
[   10.508895] CPU1 attaching NULL sched-domain.
[   10.620577] CPU0 attaching sched-domain:
--
[   13.100193] CPU1 attaching sched-domain:
[   13.100195]  domain 0: span 0-1 level MC
[   13.100197]   groups: 1 0
[   14.387617] hda-intel: Invalid position buffer, using LPIB read method instead.
[   14.387631] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   20.788016] eth2: no IPv6 routers present
[   20.851777] sr 0:0:1:0: [sr0] Unhandled sense code
[   20.851781] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   20.851785] sr 0:0:1:0: [sr0] Sense Key : Medium Error [current] 

```
 [COLOR=Red]linux discovered a RTL8169sc/8110sc card in the machine[/COLOR]

3. route
```

140.112.61.0    *               255.255.255.0   U     1      0        0 eth2
link-local      *               255.255.0.0     U     1000   0        0 eth2

```
4. cat /proc/interrupts
```

           CPU0       CPU1       
  0:         46         10   IO-APIC-edge      timer
  1:          0          2   IO-APIC-edge      i8042
  3:          0          2   IO-APIC-edge    
  6:          0          5   IO-APIC-edge      floppy
  7:          1          0   IO-APIC-edge      parport0
  8:          0          1   IO-APIC-edge      rtc0
  9:          0          3   IO-APIC-fasteoi   acpi
 14:          4      10696   IO-APIC-edge      pata_atiixp
 15:          0          0   IO-APIC-edge      pata_atiixp
 16:          3       2018   IO-APIC-fasteoi   ohci_hcd:usb2, HDA Intel
 17:          0          1   IO-APIC-fasteoi   ohci_hcd:usb3, ohci_hcd:usb5
 18:       1373        533   IO-APIC-fasteoi   ohci_hcd:usb4, ohci_hcd:usb6, radeon
 19:          0       3543   IO-APIC-fasteoi   ehci_hcd:usb1, HDA Intel
 22:       6313       4025   IO-APIC-fasteoi   ahci, ohci1394
 23:      11812         55   IO-APIC-fasteoi   eth2
NMI:          0          0   Non-maskable interrupts
LOC:      45383      94046   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
PND:          0          0   Performance pending work
RES:      43498      49047   Rescheduling interrupts
CAL:        122         48   Function call interrupts
TLB:        368        479   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:         10         10   Machine check polls
ERR:          1
MIS:          0

```
5. cat /proc/ioports
```

0000-001f : dma1
0020-0021 : pic1
0040-0043 : timer0
0050-0053 : timer1
0060-0060 : keyboard
0064-0064 : keyboard
0070-0073 : rtc0
0080-008f : dma page reg
00a0-00a1 : pic2
00c0-00df : dma2
00f0-00ff : fpu
0170-0177 : 0000:00:14.1
  0170-0177 : pata_atiixp
01f0-01f7 : 0000:00:14.1
  01f0-01f7 : pata_atiixp
0220-0225 : pnp 00:01
0228-022f : pnp 00:02
0238-023f : pnp 00:02
0290-0294 : pnp 00:01
02f8-02ff : serial
0376-0376 : 0000:00:14.1
  0376-0376 : pata_atiixp
0378-037a : parport0
03c0-03df : vga+
03f2-03f2 : floppy
03f4-03f5 : floppy
03f6-03f6 : 0000:00:14.1
  03f6-03f6 : pata_atiixp
03f7-03f7 : floppy
040b-040b : pnp 00:02
04d0-04d1 : pnp 00:01
04d6-04d6 : pnp 00:02
0b00-0b0f : 0000:00:14.0
  0b00-0b07 : piix4_smbus
0c00-0c01 : pnp 00:02
0c14-0c14 : pnp 00:02
0c50-0c52 : pnp 00:02
0c6c-0c6d : pnp 00:02
0c6f-0c6f : pnp 00:02
0cd0-0cd1 : pnp 00:02
0cd2-0cd3 : pnp 00:02
0cd4-0cdf : pnp 00:02
0cf8-0cff : PCI conf1
4000-40fe : pnp 00:02
  4000-4003 : ACPI PM1a_EVT_BLK
  4004-4005 : ACPI PM1a_CNT_BLK
  4008-400b : ACPI PM_TMR
  4010-4015 : ACPI CPU throttle
  4020-4027 : ACPI GPE0_BLK
  4050-4050 : ACPI PM2_CNT_BLK
4100-411f : pnp 00:02
4210-4217 : pnp 00:02
d000-dfff : PCI Bus 0000:02
  de00-deff : 0000:02:0f.0
    de00-deff : r8169
e000-efff : PCI Bus 0000:01
  ee00-eeff : 0000:01:05.0
f900-f90f : 0000:00:14.1
  f900-f90f : pata_atiixp
fb00-fb0f : 0000:00:12.0
  fb00-fb0f : ahci
fc00-fc03 : 0000:00:12.0
  fc00-fc03 : ahci
fd00-fd07 : 0000:00:12.0
  fd00-fd07 : ahci
fe00-fe03 : 0000:00:12.0
  fe00-fe03 : ahci
ff00-ff07 : 0000:00:12.0
  ff00-ff07 : ahci

```

---

### Post by IcarusR on 2011-02-12
> [ 9.150142] udev: renamed network interface eth0 to eth2

So you will need to use eth2 not eth0.

Can you ping your router by ip ?

Assuming you quoted all of the output of 'route'

> 140.112.61.0 * 255.255.255.0 U 1 0 0 eth2
link-local * 255.255.0.0 U 1000 0 0 eth2


Then you are missing the gateway

My output of 'route' is

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
xxx.xxx.1.0     *               255.255.255.0   U     1      0        0 eth0
xxx.xxx.1.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         O2WirelessBox.l 0.0.0.0         UG    0      0        0 eth0
```

I can ping O2WirelessBox

From the route man page

> route add default gw mango-gw
              adds  a  default  route (which will be used if no other route matches).  All packets using this route will be gatewayed through "mango-gw".
              The device which will actually be used for that route depends on how we can reach "mango-gw" - the static route to "mango-gw" will have  to
              be set up before.


You need to add a route to the gateway. Run the following, of course you need to substitute your gateway ip or name.

```
route add default gw <gaddr> eth2
```

This is all explained in the link you posted.

If you put command outputs in the 'code' wrappers the format is retained making it much easier to read.

---

### Post by yushengc on 2011-02-12
Thanks for replying! I'm so sorry that I posted incomplete results of route. I still cannot connect to the internet. The results of route instruction are

```

[SIZE="1"]
Destination     Gateway        Genmask       Flags Metric Ref Use Iface
140.112.61.0    *              255.255.255.0 U     1      0 0 eth2
link-local      *              255.255.0.0   U     1000   0 0 eth2
default         140.112.61.254 0.0.0.0       UG    0      0 0 eth2
[/SIZE]

```

Here are some more information

tracepath [www.google.com](www.google.com)
```

gethostbyname2: Unkown host

```

tracepath 140.112.61.254(gateway)
```

1: irod.local (140.112.61.75) 0.246ms pmtu 1500
1: no reply
2: no reply
3: no reply
4: no reply

```

less /etc/resolv.conf
```

#Generated by NetworkManager
nameserver 8.8.8.8

```

less /etc/networks
```

# symbolic names for networks, see networks(5) for more information
link-local 169.254.0.0

```

---

### Post by KyferEz on 2012-06-29
Did you ever solve this? I am having the EXACT same problem. Here's the link to my post: 
[http://ubuntuforums.org/showthread.php?p=12064071](http://ubuntuforums.org/showthread.php?p=12064071)

Did you by chance install Ubuntu with no network connection? I had my network disconnected and am starting to think that may have something to do with it.

---

### Post by SparTacux on 2012-06-30
It could be an ARP issue. I had a dodgy connection to a router on one laptop and fixed the problem by using a static arp table on that laptop.

 Use arp -s <ip-address> <mac address >

Download wireshark and try and find out what's happening.

---

