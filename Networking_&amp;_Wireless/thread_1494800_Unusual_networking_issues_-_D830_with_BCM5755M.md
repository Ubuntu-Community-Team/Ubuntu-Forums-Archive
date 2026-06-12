---
title: "Unusual networking issues - D830 with BCM5755M"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by Dr. Phatbeats on 2010-05-27
Hi all,

I've been having some very strange networking issues. I thought it was a VirtualBox problem, so I did a complete rebuild. The problem persisted. All the info from here is obtained booting in a live CD (10.04 Desktop x86).

The problem:
Wired Networking. Packets go out, but "come back" with a different MAC address.  Anything below the IP layer works fine. For example:

```
May 27 14:05:11 ubuntu NetworkManager: <info>  DHCP: device eth0 state changed (
null) -> preinit
May 27 14:05:11 ubuntu dhclient: Listening on LPF/eth0/00:1d:09:cc:73:08
May 27 14:05:11 ubuntu dhclient: Sending on   LPF/eth0/00:1d:09:cc:73:08
May 27 14:05:11 ubuntu dhclient: Sending on   Socket/fallback
May 27 14:05:14 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67
 interval 7
May 27 14:05:21 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67
 interval 15
May 27 14:05:21 ubuntu dhclient: DHCPOFFER of x.x.x.116 from x.x.x.4
May 27 14:05:21 ubuntu dhclient: DHCPREQUEST of x.x.x.116 on eth0 to 255.255
.255.255 port 67
May 27 14:05:21 ubuntu dhclient: DHCPACK of x.x.x.116 from x.x.x.4
May 27 14:05:21 ubuntu dhclient: bound to x.x.x.116 -- renewal in 6082 secon
ds.
```Great so far!! Then I do this:

```
ubuntu@ubuntu:~$ ping x.x.x.1
PING x.x.x.1 (x.x.x.1) 56(84) bytes of data.
```And nothing happens. tcpdumping it:

```

14:36:03.658100 AMAC:08 > BMAC:01, ethertype IPv4 (0x0800), length 98: x.x.x.116 > x.x.x.x.1: ICMP echo request, id 54033, seq 1740, length 64

14:36:03.658383 CMAC:8b > DMAC:ca, ethertype IPv4 (0x0800), length 98: v1 > x.x.x.116: ICMP echo reply, id 54033, seq 1740, length 64

14:36:04.666115 AMAC:08 > BMAC:01, ethertype IPv4 (0x0800), length 98: x.x.x.116 > x.x.x.1: ICMP echo request, id 54033, seq 1741, length 64

14:36:04.666380 CMAC:8b > DMAC:ca, ethertype IPv4 (0x0800), length 98: x.x.x.1 > x.x.x.116: ICMP echo reply, id 54033, seq 1741, length 64
```We use some kind of fail over setup, which is why BMAC and CMAC are different. But the problem is obviously that AMAC != DMAC hence they all just get dropped. I've chatted to our network team and they assure me it's not a network problem. So I'm left thinking it's a host issue. This has cost me a MASSIVE amount of head scratching time and I'm clear outa ideas. Some info:

```

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

ubuntu@ubuntu:~$ cat /etc/issue
Ubuntu 10.04 LTS \n \l

ubuntu@ubuntu:~$ sudo lspci -vv | less
...
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
        Subsystem: Dell Device 01fe
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 30
        Region 0: Memory at f9bf0000 (64-bit, non-prefetchable) [size=64K]
        Expansion ROM at <ignored> [disabled]
        Capabilities: [48] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=1 PME-
        Capabilities: [50] Vital Product Data <?>
        Capabilities: [58] Vendor Specific Information <?>
        Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
                Address: 00000000fee0200c  Data: 41a9
        Capabilities: [d0] Express (v1) Endpoint, MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
                        ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                        MaxPayload 128 bytes, MaxReadReq 4096 bytes
                DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <4us, L1 <64us
                        ClockPM+ Suprise- LLActRep- BwNot-
                LnkCtl: ASPM L0s Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [13c] Virtual Channel <?>
        Capabilities: [160] Device Serial Number xxxxxxxxx
        Capabilities: [16c] Power Budgeting <?>
        Kernel driver in use: tg3
        Kernel modules: tg3

ubuntu@ubuntu:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr AMAC:08  
          inet addr:x.x.x.116  Bcast:x.x.x.255  Mask:255.255.255.0
          inet6 addr:xxxxx:7308/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5607 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1693 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:492571 (492.5 KB)  TX bytes:172052 (172.0 KB)
          Interrupt:17

ubuntu@ubuntu:~$ dmesg | grep tg3
[    3.905177] tg3.c:v3.102 (September 1, 2009)
[    3.905197] tg3 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.905208] tg3 0000:09:00.0: setting latency timer to 64
[   63.805713] tg3 0000:09:00.0: irq 30 for MSI/MSI-X
[  176.324197] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  176.324201] tg3: eth0: Flow control is off for TX and off for RX.
[ 2030.067099] tg3: eth0: Link is down.


 
```Does anyone have any suggestions? My current thought is either flaky hardware or me doing some really really stupid that is really really obvious?

Al

---

### Post by Dr. Phatbeats on 2010-05-27
Update:  While venting to a team member, they mentioned we had a spare D830. I fired it up with the same live CD, and got exactly the same issue (although obviously it had a different MAC address, but the return MAC address was still different).  I am terribly confused. Hardware has now been ruled out?  At what point should I file a bug?  Cheers, Al

---

