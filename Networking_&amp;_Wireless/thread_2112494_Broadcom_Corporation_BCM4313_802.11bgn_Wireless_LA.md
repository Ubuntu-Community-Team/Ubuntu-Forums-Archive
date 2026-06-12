---
title: "Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727]"
date: 2013-02-04
forum: Networking &amp; Wireless
---

### Post by waterguy on 2013-02-04
Until about 5 days ago it worked fine then it updated and here I am.  
I have spent the last 5 days trying to understand all the threads about the BCM4313.  then again my problem is yes i see the wifi networks and can connect to non-secure networks.  I can not connect to my WPA2 secured network.  All other laptops, smart-phones, printers, and Sony streamers work perfect in WPA2 secured connection.
lspci -vvnn returns the following

                                                             02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01) 
     Subsystem: Foxconn International, Inc. Device [105b:e042] 
     Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
     Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
     Latency: 0, Cache Line Size: 64 bytes 
     Interrupt: pin A routed to IRQ 17 
     Region 0: Memory at c4000000 (64-bit, non-prefetchable) [size=16K] 
     Capabilities: <access denied> 
     Kernel driver in use: wl 
     Kernel modules: wl, bcma, brcmsmac
  
The machine Acer Aspire One D270-1375 Intel Atom N2600 
Running 12.04 32 bit
Help???

---

### Post by varunendra on 2013-02-04
Welcome to the forums waterguy! :)

Please take a look at this thread: [http://ubuntuforums.org/showthread.php?t=2112259](http://ubuntuforums.org/showthread.php?t=2112259)

This one is a possible bug in the driver included in latest updates.
Try the suggested workaround in post #5 or post #8 there

---

### Post by waterguy on 2013-02-06
Ok i did this thread: [http://ubuntuforums.org/showthread.php?t=2112259](http://ubuntuforums.org/showthread.php?t=2112259) post #5

Sort of works except does not accept the DNS information Can get it to talk to local network address's  not requiring  Non local  DNS here is the present lspci.  actually to post this now getting through by going to the non-secure connection.

```
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e042]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at c4000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: brcmsmac
    Kernel modules: wl, bcma, brcmsmac
```

---

### Post by varunendra on 2013-02-07
While I don't fully understand your current problem *(maybe bacause I'm in a hurry right now)*, the OP in the referred thread actually got his problem solved by following mikewhatever's solution here : [http://askubuntu.com/questions/250858/broadcom-wireless-bcm4313-on-12-04-lts/250896#250896](http://askubuntu.com/questions/250858/broadcom-wireless-bcm4313-on-12-04-lts/250896#250896)

If it is not relevant, or doesn't help, please post back and we'll try to get remaining issues sorted.

Sorry for posting in a hurry, hope you get some help from the link.

---

