---
title: "Broadcom BCM4322"
date: 2012-11-30
forum: Networking &amp; Wireless
---

### Post by pyro117 on 2012-11-30
Here is my broadcom wireless information:

03:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
        Subsystem: Apple Inc. AirPort Extreme
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort+ <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 256 bytes
        Interrupt: pin A routed to IRQ 23
        Region 0: Memory at 93200000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: wl
        Kernel modules: wl, ssb

The system will see the wireless card but no wireless networks and yes i am in range.  I have tried several things mentioned on the web-site.  manually installing the BCM drivers - no luck, manually install the NDIS Wrapper - couldn't get that to work, manually installing the STA - that didn't work either.  I figure I did so much wrong in doing that - so i just re-installed Kubuntu.  

I am using Kubuntu because my son's teacher is requiring him to use it.  I can't switch to Ubuntu until his class is over. 

Oh, and I can't find where to do the "Additional Drivers".  Yes, i am that much of a noob...

---

### Post by pyro117 on 2012-11-30
I finally found the "Additional Drivers" and it says the Broadcom STA driver is installed and running - but it won't find any wireless routers still.

Can you think of anything I need to do or try?  Also, if I can't get this to work, then I will have to buy a usb based adapter - how will I know if one type will work or not?

---

### Post by sidzen on 2012-11-30
see:  [http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)

---

### Post by pyro117 on 2012-12-02
I read that, tried it and totally messed up Kubuntu.  Don't know how I did it, but it wouldn't boot after that.

I re-installed Kubuntu but this time with the wired network working.  This auto installed the STA drivers amazingly enough but what it didn't do (come to find out) is auto start the drivers.  I ran the following command:

*echo wl* | *sudo tee* -a /etc/modules

now, the wireless works just fine.

My next problem is every time I boot I keep getting asked for a password to open the wallet so the network manager can get access to the Wireless connection password - at least I think that is what it is doing.  I need to know how to turn this off - so annoying.

---

### Post by pyro117 on 2012-12-04
Everything is solved.  So far, I have a smooth running Kubuntu system.  Thanks for your help.

---

