---
title: "Internet not working for Ubuntu machine only"
date: 2011-08-11
forum: Networking &amp; Wireless
---

### Post by XD2 on 2011-08-11
Hi,

I have just moved into an office and set up 3 computers. 2 run windows 7 and one runs Ubuntu. The two running windows have connected to the network fine and internet works great, I am using one to post this.

However the Ubuntu machine connects to the network and shows it is connected however it won't load pages or browse the internet. I did do a ping and it actually pinged the site but with 99% loss.

The set up is there is the main broadband router which is connected to a switch which feeds the offices. I then have my own switch running from this for my own network, which as I mentioned works apart from this.

I did run this command "sudo ifconfig" and here are the results.

```

LINUX:~$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:8a:d4:b5  
          inet addr:10.25.1.17  Bcast:10.25.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:c6ff:fe8a:d4b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2754 errors:0 dropped:0 overruns:0 frame:0
          TX packets:364 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:318123 (318.1 KB)  TX bytes:43851 (43.8 KB)
          Interrupt:20 Memory:f9ec0000-f9ee0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

```

Any help or advice will be greatly appreciated.

---

### Post by coffee412 on 2011-08-11
Check to make sure its not something upstream from the ubuntu computer first: take the ubuntu computer and hook it up to one of the ethernet cables from one of the windows boxes. See if you are still having issues. If you are then atleast you are now narrowed down to the particular computer running ubuntu. Otherwise it could be a bad cable or port on your switch or something else.

---

### Post by XD2 on 2011-08-11
Sorry I should have mentioned I have tried different cables including ones that have been found to work on the windows machines, i also tried plugging the Ubuntu box directly to the port before my switch in case it was a setting there. But always the same result.

I think it is definitely a setting within the system but I am not really sure what to look for.

Thanks for your fast reply though.

---

### Post by coffee412 on 2011-08-11
Ok. Well, What bothers me is that you said that you got 90 percent packet loss. 

Can you ping one of the windows boxes ok? no errors? 

If you do a "Dmesg |grep eth0" what does it show?

coffee

---

### Post by XD2 on 2011-08-11
Here is the ping results:
```

LINUX:~$ ping -c 10 xd2.net
PING xd2.net (78.129.202.160) 56(84) bytes of data.
64 bytes from xd2.net (78.129.202.160): icmp_req=1 ttl=51 time=21.3 ms

--- xd2.net ping statistics ---
10 packets transmitted, 1 received, 90% packet loss, time 13025ms
rtt min/avg/max/mdev = 21.377/21.377/21.377/0.000 ms
LINUX:~$ ping -c 10 10.25.1.1
PING 10.25.1.1 (10.25.1.1) 56(84) bytes of data.
64 bytes from 10.25.1.1: icmp_req=1 ttl=64 time=5.19 ms
64 bytes from 10.25.1.1: icmp_req=2 ttl=64 time=1.07 ms
64 bytes from 10.25.1.1: icmp_req=3 ttl=64 time=1.05 ms
64 bytes from 10.25.1.1: icmp_req=4 ttl=64 time=1.04 ms
64 bytes from 10.25.1.1: icmp_req=5 ttl=64 time=1.09 ms
64 bytes from 10.25.1.1: icmp_req=6 ttl=64 time=1.03 ms
64 bytes from 10.25.1.1: icmp_req=7 ttl=64 time=1.05 ms
64 bytes from 10.25.1.1: icmp_req=8 ttl=64 time=1.04 ms
64 bytes from 10.25.1.1: icmp_req=9 ttl=64 time=1.04 ms
64 bytes from 10.25.1.1: icmp_req=10 ttl=64 time=1.04 ms

--- 10.25.1.1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9009ms
rtt min/avg/max/mdev = 1.034/1.467/5.195/1.243 ms

```I will run that other command and get the results now I had already done this as I seen your post, I have to keep putting them on a USB drive to post them here :-)

EDIT: The first one is my website on the internet, the second is the local network.

---

### Post by XD2 on 2011-08-11
The Dmesg |grep eth0 command returns command not found.

By the way i am using Ubuntu 11.04 Natty Narwhal.

Thanks.

---

### Post by coffee412 on 2011-08-11
try this instead sorry for the cap D

> dmesg |grep eth0

and also

 > lspci -vv 

Cannot help unless I know what we are working with?

---

### Post by XD2 on 2011-08-11
Sorry didn't think to remove the cap D :-\ 

dmesg |grep eth0
```
LINUX:~$ dmesg |grep eth0
[    1.322337] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1f:c6:8a:d4:b5
[    1.322340] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.322366] e1000e 0000:00:19.0: eth0: MAC: 7, PHY: 6, PBA No: FFFFFF-0FF
[   27.584320] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.884879] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   28.884884] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   28.885050] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   39.032015] eth0: no IPv6 routers present
```

lspci -vv
```
LINUX:~$ lspci -vv
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a5d
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fa000000-febfffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:19.0 Ethernet controller: Intel Corporation 82566DC-2 Gigabit Network Connection (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a5d
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 42
    Region 0: Memory at f9ec0000 (32-bit, non-prefetchable) [size=128K]
    Region 1: Memory at f9efd000 (32-bit, non-prefetchable) [size=4K]
    Region 2: I/O ports at c080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 2a5d
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 4: I/O ports at c400 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 2a5d
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 21
    Region 4: I/O ports at c480 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 2a5d
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 18
    Region 0: Memory at f9efec00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a5d
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 43
    Region 0: Memory at f9ef4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 2a5d
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 23
    Region 4: I/O ports at c800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 2a5d
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 19
    Region 4: I/O ports at c880 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 2a5d
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 18
    Region 4: I/O ports at cc00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 2a5d
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin D routed to IRQ 16
    Region 4: I/O ports at d000 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 2a5d
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 23
    Region 0: Memory at f9eff800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01 [Subtractive decode])
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    Memory behind bridge: f9f00000-f9ffffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a5d
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a5d
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 41
    Region 0: I/O ports at d880 [size=8]
    Region 1: I/O ports at d800 [size=4]
    Region 2: I/O ports at d480 [size=8]
    Region 3: I/O ports at d400 [size=4]
    Region 4: I/O ports at d080 [size=32]
    Region 5: Memory at f9eff000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a5d
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin C routed to IRQ 5
    Region 0: Memory at f9effc00 (64-bit, non-prefetchable) [size=256]
    Region 4: I/O ports at 0400 [size=32]
    Kernel modules: i2c-i801

01:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70) (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 2a5d
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (3000ns min, 6000ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 20
    Region 0: Memory at f9fff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9300 GE] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Device 1b0a:9004
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Region 3: Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
    Region 5: I/O ports at ec00 [size=128]
    [virtual] Expansion ROM at febe0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb
```

---

### Post by coffee412 on 2011-08-11
Ok, Everything looks good in the dmesg output and shows an intel e1000 nic. 

Are the DNS addresses the same when comparing the win7 boxes and the Ubuntu box? 

1. Pinging one of the win7 boxes do you get good pings?
2. Pinging your DNS entries, Good or Bad?
3. Pinging your gateway - Good Bad?

If they are all bad then there is some issue with possibly the nic on the ubuntu computer. I would try adding another card temporarily and see if it improves things.

coffee

---

### Post by XD2 on 2011-08-11
Pinging the computer I am on now:
```
LINUX:~$ ping -c 10 10.25.1.40
PING 10.25.1.40 (10.25.1.40) 56(84) bytes of data.
64 bytes from 10.25.1.40: icmp_req=1 ttl=128 time=4.80 ms

--- 10.25.1.40 ping statistics ---
10 packets transmitted, 1 received, 90% packet loss, time 9064ms
rtt min/avg/max/mdev = 4.804/4.804/4.804/0.000 ms

```

The gateway for the router:
```
LINUX:~$ ping -c 10 10.25.1.2
PING 10.25.1.2 (10.25.1.2) 56(84) bytes of data.

--- 10.25.1.2 ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9072ms
```

The DNS (listed nameserver on ubuntu also)
```
LINUX:~$ ping -c 10 10.25.1.251
PING 10.25.1.251 (10.25.1.251) 56(84) bytes of data.
64 bytes from 10.25.1.251: icmp_req=1 ttl=128 time=0.275 ms
64 bytes from 10.25.1.251: icmp_req=2 ttl=128 time=0.508 ms
64 bytes from 10.25.1.251: icmp_req=3 ttl=128 time=0.264 ms
64 bytes from 10.25.1.251: icmp_req=4 ttl=128 time=0.258 ms
64 bytes from 10.25.1.251: icmp_req=5 ttl=128 time=0.259 ms
64 bytes from 10.25.1.251: icmp_req=6 ttl=128 time=0.506 ms
64 bytes from 10.25.1.251: icmp_req=7 ttl=128 time=0.255 ms
64 bytes from 10.25.1.251: icmp_req=8 ttl=128 time=0.257 ms
64 bytes from 10.25.1.251: icmp_req=9 ttl=128 time=0.256 ms
64 bytes from 10.25.1.251: icmp_req=10 ttl=128 time=0.256 ms

--- 10.25.1.251 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 8998ms
rtt min/avg/max/mdev = 0.255/0.309/0.508/0.100 ms
```

I am near 100% sure the network card works as it was only moved to the office yesterday and it functions fine on my home network.

Thanks again for your help.

---

### Post by coffee412 on 2011-08-11
That is very weird. Pinging your eth0 gives packet loss. Pinging DNS shows no packet loss.

Doesnt make sense. So, If it doesnt make sense then this must be a problem with 11.04 / kernel / driver. I would at this point fireup a bootable cd of maybe 10.04 and check the connection from the live cd. Then we know its not a hardware issue and is something to do with 11.04

That is the best I can do for you. Without doing that we will be hard pressed to find the problem.

---

### Post by XD2 on 2011-08-11
Ok I will have a go at that, will I have to make a bootable CD then as I don't have one, can I do this just by downloading that version from the site? I will figure it out.

Thanks again, it really is appreciated.

---

### Post by coffee412 on 2011-08-11
Yes, You should be able to find one from Ubuntu's site. To be honest, Im not a big fan of 11.04 and this unity stuff. I run 10.04 in a Virtualbox setup ontop of Fedora 14. 

Let me know what happens. Got my curiosity up now :P

---

### Post by XD2 on 2011-08-11
I created a bootable USB for 10.04 but it didn't help still same situation with pings and internet connection so I really am lost with what to do or try at this point, might have to switch this machine back to windows.

---

### Post by coffee412 on 2011-08-11
> **XD2 said:**
> I created a bootable USB for 10.04 but it didn't help still same situation with pings and internet connection so I really am lost with what to do or try at this point, might have to switch this machine back to windows.

Replace the network card. They are not very expensive. It will probably give you problems if you install windows too.

---

### Post by XD2 on 2011-08-11
Quick update after messing about a bit, if I disconnect from the network and then reconnect I can browse maybe 4 or 5 pages on the internet and they load really fast and then it flakes out again.

Would this still indicate a network card issue. or more on the software side. I can pick up another network card. I might actually have one lying around somewhere.

Just thought I would mention it.

---

### Post by XD2 on 2011-08-11
As and example I reconnected to the lan and ran this command one after another literally as the first finish I re-ran it:
```
LINUX:~$ ping -c 10 xd2.net
PING xd2.net (78.129.202.160) 56(84) bytes of data.
64 bytes from xd2.net (78.129.202.160): icmp_req=1 ttl=51 time=18.7 ms
64 bytes from xd2.net (78.129.202.160): icmp_req=2 ttl=52 time=15.6 ms
64 bytes from xd2.net (78.129.202.160): icmp_req=3 ttl=52 time=15.7 ms
64 bytes from xd2.net (78.129.202.160): icmp_req=4 ttl=52 time=15.8 ms
64 bytes from xd2.net (78.129.202.160): icmp_req=5 ttl=52 time=15.5 ms
64 bytes from xd2.net (78.129.202.160): icmp_req=6 ttl=52 time=15.7 ms
64 bytes from xd2.net (78.129.202.160): icmp_req=7 ttl=52 time=15.5 ms
64 bytes from xd2.net (78.129.202.160): icmp_req=8 ttl=52 time=15.4 ms
64 bytes from xd2.net (78.129.202.160): icmp_req=9 ttl=52 time=15.2 ms
64 bytes from xd2.net (78.129.202.160): icmp_req=10 ttl=52 time=15.8 ms

--- xd2.net ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9013ms
rtt min/avg/max/mdev = 15.286/15.944/18.764/0.969 ms
```

```
LINUX:~$ ping -c 10 xd2.net
PING xd2.net (78.129.202.160) 56(84) bytes of data.

--- xd2.net ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9071ms
```

---

### Post by coffee412 on 2011-08-11
If you have another nic laying around I would put it in and reconfigure. Did you ever boot from a cd (10.04) and try it? I would do that first. Then when you put in the other card make sure you go into your bios and turn off the first one. Then reboot and setup the new card.

coffee

---

### Post by Johnb0y on 2011-08-11
just a quick q... did you try and replace/update the drivers for the NIC?

---

### Post by XD2 on 2011-08-12
Hey, thanks again for the replies I will try both of these things today and post here the results if any.

---

### Post by XD2 on 2011-08-12
Ok first I tried updating the drivers which didn't change anything but I could still connect and load a page in the first 5 seconds. Then i bought a new card and installed that, and ran the drivers it picked up the network like the old one but no internet at all on this one.

Strangely it shows two connections on the top right.
1. Auto eth0 (this does nothing)
2. Auto Ethernet (this allows a few seconds of browsing when first connected to)

I also tried blacklisting ipv6 as I read that could cause problems, but this hasn't resolved anything either.

Thanks again.

---

### Post by coffee412 on 2011-08-12
YOu have a very strange situation here. Basically I have never heard of a problem like yours. I would like to look over some points first as to recap your situation.

1. Lets take a look at your file /etc/resolv.conf

> cat /etc/resolv.conf
resolv.conf should list 2 ip addresses and they should be your DNS servers. Please compare these to your windows boxes to make sure they are the same. If they are not then change them to match your windows boxes.

2. Did you boot from 10.04 and have the same situation again?

Ill be back on later this afternoon and will go over your posts again looking for some more clues.

coffee

---

### Post by XD2 on 2011-08-12
Hey,

Funly you should mention resolv.conf before reading this I was trying some stuff and noticed the ip in there was set my Network Manager. Everytime I set it to OpenDNS IP it worked for seconds before Network manager reset it. I am trying to find out how to stop this I disables Network manager but now don't know how to manage the network lol.

I did try a 10.04 boot from USB and also an 11.04 fresh boot from usb both have the same problem. I presume it is a dns issue on the nameserver, maybe it is picking up the wrong one from the router. so maybe figuring out how to stop it being reverted will solve my problem.

---

### Post by coffee412 on 2011-08-12
yes, go into networkmanager by right or left clicking on it and choose edit connection and change your dns settings.

That should put this baby to bed!

---

### Post by XD2 on 2011-08-13
I can't actually find Network manager, it says it is installed but there is no System > Administrator > Network menu item. And when i tried to disable it to stop resolv.conf being changed it removed from the top bar but I will try on the usb boot if that fixes it I will try and reinstall it.

Thanks again for all your help.

---

### Post by XD2 on 2011-08-13
Feels good to announce I am posting this from the Linux Box. I did the setup manually changed the DNS to OpenDNS and also changed the default gateway from X.X.1.2 to X.X.1.1 so it forced these settings on connection, and once again life is good.

I cannot thank you enough for your help as I never would have figured this out without your guidance. If there is anything I can do to return the favor let me know.

Mark as solved??

---

### Post by coffee412 on 2011-08-13
Yes! Congradulations!

Glad to hear that you got your problem worked out. You owe me nothing but the possibility of in the future you help someone else out when they have problems. Kinda like pay it forward.

Have a great weekend!

ps - Make sure to mark your problem post SOLVED.:popcorn:

coffee

---

