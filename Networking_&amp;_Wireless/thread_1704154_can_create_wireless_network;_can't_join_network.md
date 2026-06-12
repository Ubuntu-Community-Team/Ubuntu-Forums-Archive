---
title: "can *create* wireless network; can't *join* network"
date: 2011-03-10
forum: Networking &amp; Wireless
---

### Post by gac_1959 on 2011-03-10
Hi.  I've got two computers sitting next to each other.  The new one has  only Maverick (10.10) installed (clean disk wipe) in January.  The  older (18 months) one is an iMac running Snow Leopard.  Both are  up-to-date software-wise. I have one wired DSL connection available.

Here's  what works: if I plug the ethernet cable from the DSL modem into the  linux box, and "create new wireless network" (Linksys WMP600N wireless  card) with net manager (specifying WEP), and turn AirPort on in the  iMac, it can see the new network, join with it, and browse the web at  will via the shared connection.  All is well so far.

Here's what  sadly doesn't work: reverse the setup by plugging the wired connection  into the iMac, have *it* create a network, and have the linux box try to  join.  The iMac is happily surfing with the wired connection.  The  linux box (net manager) just keeps re-prompting me for a password every  minute or so, never connecting.  Unfortunately this connectivity would  be much preferable for from a cabling and physical perspective, so I'm  motivated to get it working this way.

Here's what I've tried to get the latter configuration working, all without success:
- Turn firewalls completely off on both machines.  Obviously this wouldn't have been a viable long-term solution anyway.
-  With firewalls both on or off, turn off WEP encryption.  Again, another  non-starter for the long term; just grasping at straws really...
-  Searched forums and found out about "wicd".  Installed it; no better  luck than with NM.  It did report "bad password" when I was in the WEP  configuration, and "unable to get IP address" when in the unsecured  configuration.  Naturally I know the password I supplied is valid, and  that "internet sharing" was turned on on the iMac.  I have since removed  wicd via the Software Center.

Info about the linux box:

```
% lspci -vv    (edited to remove non-wireless info)
01:09.0 Network controller: RaLink RT2800 802.11n PCI
    Subsystem: Linksys Device 0067
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (500ns min, 1000ns max), Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at f9ff0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2800pci
    Kernel modules: rt2860sta, rt2800pci

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"xxxx"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: F2:DB:4C:22:B6:81   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
$ uname -mr
2.6.35-27-generic x86_64

Here  are some boot-time error messages, but these occur whether I'm in the  working or the non-working network config, so may not be relevant:

[   45.211574] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0x05100000
[   45.231746] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware

```I  do see some "DHCPDISCOVER wlan0..." messages in the syslog while I'm  trying to join the network, with various timeouts.  Eventually I get a  "DHCPv4 request timed out" message, followed by other messages  indicating it's giving up.  So really I don't know if the issue is on  the Mac machine or the Ubuntu machine.  Sigh.

Anyway, I greatly  appreciate these forums and all the help and clues that have been  provided so far in my first foray into the Ubuntu world.

--Gary

---

### Post by faixan on 2012-01-09
> **gac_1959 said:**
> Hi.  I've got two computers sitting next to each other.  The new one has  only Maverick (10.10) installed (clean disk wipe) in January.  The  older (18 months) one is an iMac running Snow Leopard.  Both are  up-to-date software-wise. I have one wired DSL connection available.

Here's  what works: if I plug the ethernet cable from the DSL modem into the  linux box, and "create new wireless network" (Linksys WMP600N wireless  card) with net manager (specifying WEP), and turn AirPort on in the  iMac, it can see the new network, join with it, and browse the web at  will via the shared connection.  All is well so far.





please can you describe step by step process for how you did this?
i'm trying the same thing, network is sucessfully created and even detected in Win7 on another machine i've at home, but it doesn't recognise the "passkey" :s :(

---

