---
title: "Detecting fax"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by RCepeda on 2009-12-30
Hello everyone!
I have been searching the internet and this forum as well for a fix to another little problem that I am having. I am trying to set up hylafax server and I have downloaded all of the packages that I needed and as far as I believe I have everything I need. My problem is that I can not detect my modem. This is what I have done so far:

I have used the lspci -vv command and I got a bunch of info, but I'm not going to bore you with all that. This is what I got for the modem:

03:06.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
    Subsystem: Conexant Systems, Inc. Device 200c
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at fdce0000 (32-bit, non-prefetchable) [size=64K]
    Region 1: I/O ports at cf00 [size=8]
    Capabilities: <access denied>

I have also done this how to and nothing still:

randolc@server:~/Documents$ gunzip scanModem.gz
randolc@server:~/Documents$ chmod +x scanModem
randolc@server:~/Documents$ ./scanModem
UPDATE=2009_12_26
 Continuing as this update is only 1 weeks old,
 but the current Update is always at: [http://linmodems.technion.ac.il](http://linmodems.technion.ac.il)

grep: 01:05.1: No such file or directory
grep: 01:05.1: No such file or directory

I also just ran faxsetup command and it got the the part that I needed to add a fax modem and it asked me to enter the correct ttsy for the serial port and I don't know what that is either.

I also have been reading that it might be because of the modem not being compatible with linux due to no driver. :confused:
Thank you in advance!!!

---

