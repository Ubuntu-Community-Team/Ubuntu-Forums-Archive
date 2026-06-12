---
title: "linksys WPC54G ver 5 problem!"
date: 2009-07-21
forum: Networking &amp; Wireless
---

### Post by daviddoeschl on 2009-07-21
Hi all, i am really new to linux, I installed ubunto on my old laptop to make it run quicker. Only problem is my network card (linksys wpc54g ver. 5) is not supported. So i used ndiswrapper to install the drivers, and the power light flashes on the network card. I can also view my local wireless networks but for some wierd reason cannot connect to them! I have installed ndisgtk and when i go to 
system-administration- windows wireless drivers 
It comes up with a warning message (with my network card connected)
CANNOT SEE IF HARDWARE IS PRESENT.

Please help me on this as this is the deciding factor that could push me back to dreaded windows XP:(
THANKS
David Wilson

---

### Post by Metaljaz on 2009-07-21
Post the results of this command run from the terminal window (terminal window is located under Applications>Accessories>Terminal):

lscpi

It should look something like this:

Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by russtoku on 2009-08-11
I also have a Linksys WPC54G ver. 5 PCMCIA card that I'm trying to get to work with Ubuntu 9.04.

lscpi:

16:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

lspci -vv:

16:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
        Subsystem: Linksys Device 0040
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at 80000000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Region 1: Memory at 80010000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

It's not a Broadcom chip.

Thanks,
Russ

---

### Post by russtoku on 2009-08-11
Oh, if I would have read a few more google lines I would have seen a 09/20/2008 post that says this problem is solved.

**SOLVED: Linksys WPC54G v5 active but won't connect**
[http://ubuntuforums.org/showthread.php?t=925775](http://ubuntuforums.org/showthread.php?t=925775)

I haven't tried it yet but I also grabbed the Cisco Linksys driver from:

[http://www.linksysbycisco.com/US/en/support/WPC54G/download](http://www.linksysbycisco.com/US/en/support/WPC54G/download)

which is not what's attached to that post. The attachment to that post is just the INF file and doesn't include the SYS file. I believe that both are needed.

Russ

---

### Post by russtoku on 2009-08-11
There's also this 02/09/2007 post in the Linksys Communit Forums that says the Cisco Linksys driver for the version 5 card works and says how:

WPC54Gv5 slow speed issue
[http://forums.linksys.com/linksys/board/message?board.id=Wireless_Adapters&message.id=4131](http://forums.linksys.com/linksys/board/message?board.id=Wireless_Adapters&message.id=4131)

Hope this helps,
Russ

---

### Post by russtoku on 2009-08-11
OK, I tried the posts that I found:

**SOLVED: Linksys WPC54G v5 active but won't connect** -- doesn't work at all; the inf file by itself isn't enough

**WPC54Gv5 slow speed issue** -- works in that the wlan0 device is created but I can't connect to any access point via Network Manager

Hope this helps,
Russ

---

### Post by russtoku on 2009-08-11
Got it working!

More googling for "wireless marvel 8335 chip" brought back:

Marvell 8335 Chipset: The State of the Union (10/03/2007)

[http://www.google.com/url?sa=t&source=web&ct=res&cd=4&url=http%3A%2F%2Fadministratosphere.wordpress.com%2F2007%2F10%2F03%2Fmarvell-8335-chipset-the-state-of-the-union%2F&ei=LOSBSt3DM4WqtgPam9XvCA&usg=AFQjCNFnlAOCVZqktYPudu7nCcbuC1ZNAw](http://www.google.com/url?sa=t&source=web&ct=res&cd=4&url=http%3A%2F%2Fadministratosphere.wordpress.com%2F2007%2F10%2F03%2Fmarvell-8335-chipset-the-state-of-the-union%2F&ei=LOSBSt3DM4WqtgPam9XvCA&usg=AFQjCNFnlAOCVZqktYPudu7nCcbuC1ZNAw)

which led to 

[https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k](https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k)

I downloaded the driver files suggested there and loaded them with the ndiswrapper and things are working on our open wireless access point.

These commands show that things are working:

$ ifconfig wlan0
$ iwconfig wlan0
$ iwlist wlan0 scanning

and when you're connected to the Internet via an access point:

$ ifconfig wlan0
$ netstat -rn

Hope this helps,
Russ

---

