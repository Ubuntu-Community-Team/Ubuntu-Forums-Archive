---
title: "Broadcom wireless being recognized as Atheros?"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by swornbrother on 2009-01-17
Hi guys, I just bought a new Compaq Presario CQ60-215dx notebook, and I've been having major troubles with getting the wireless going.

Here are the specifications:
> 
 Product Name    	 CQ60-215DX
Product Number 	NB276UA#ABA
Microprocessor 	2.00 GHz AMD Athlon X2 QL-62 Dual-Core Processor
Microprocessor Cache 	1MB L2 Cache
Memory 	2048MB
Memory Max 	4096MB
Video Graphics 	NVIDIA GeForce 8200M
Video Memory 	Up to 895MB
Hard Drive 	250GB (5400RPM)
Multimedia Drive 	SuperMulti 8X DVD±R/RW with Double Layer Support
Display 	15.6" Diagonal High Definition HP BrightView Display (1366x768)
Fax/Modem 	High speed 56k modem
Network Card 	Integrated 10/100 Ethernet LAN
Wireless Connectivity 	

    * 802.11b/g WLAN

Sound 	Altec Lansing speakers
Keyboard 	101-key compatible
Pointing Device 	Touch Pad with On/Off button and dedicated vertical scroll Up/Down pad
PC Card Slots 	
External Ports 	

    * 5-in-1 integrated Digital Media Reader for Secure Digital cards, MultiMedia cards, Memory Stick, Memory Stick Pro, or xD Picture cards
    * 3 Universal Serial Bus (USB) 2.0
    * 1 Headphone out
    * 1 microphone-in
    * 1 VGA (15-pin)
    * 1 RJ-11 (modem)
    * 1 RJ -45 (LAN)

Dimensions 	14.88" (L) x 9.9" (D) x 13.8" (min H) -1.72" (max H)
Weight 	6.52Ibs
Security 	

    * Kensington MicroSaver lock slot
    * Power-on password
    * Accepts 3rd party security lock devices

Power 	

    * 65W AC Adapter
    * 6-Cell Lithium-Ion battery



I do not know specifically which Broadcom model it is, but the system requirements for the Windows Vista driver state this:

> 
System requirements:   		Supported Devices and Features
Broadcom 802.11 a/b/g WLAN Broadcom 802.11 b/g WLAN Broadcom 4321AG 802.11a/b/g/draft-n Wi-Fi Adapter Broadcom 4322AG 802.11a/b/g/draft-n Wi-Fi Adapter


Which tells me that it's not a Broadcom chip that b43fwcutter supports.

When running the "lspci -v | less" command, I get this:

> 
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
        Subsystem: Hewlett-Packard Company Device 137a
        Flags: fast devsel, IRQ 23
        Memory at c2000000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>
        Kernel modules: ath_pci


iwconfig gives me no wireless extensions.

I'm running 8.10 - 32bit, because I can't boot into 64bit ubuntu.  What do you guys think?

P.S. On a side note, I don't know if this will have anything to do with it, but I can't get it to work on Windows Vista anymore either since I removed their default bloatwared install, and put a stripped down version of Vista on it instead.  All the drivers except wireless will work.)

P.S.S.  Also, apparently Compaq normally uses Atheros chipsets in their notebooks, but for some reason they tossed a Broadcom in this one.

Any help appreciated, thanks!

---

### Post by swornbrother on 2009-01-17
I should also add that I've tried using ndiswrapper, but the drivers Compaq provides will not recognize my hardware.

I also tried 
> 
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo /etc/init.d/networking restart

and still no wireless..

---

### Post by swornbrother on 2009-01-17
Ok, for some reason, installing the Madwifi drivers using this tutorial..

[http://ubuntuforums.org/showthread.php?t=816780&highlight=madwifi+svn](http://ubuntuforums.org/showthread.php?t=816780&highlight=madwifi+svn)

worked, even though it's supposed to be a Broadcom chip?

My mind is blown.

---

### Post by Ayuthia on 2009-01-18
Where did you see the information about the Windows driver?  Did you go into Vista and look at the wireless driver to see what card it really is?  Compaq/HP used to use a lot of Broadcom cards, but I think that they recently switched over to Atheros.

So if you are using Vista and it shows that it is using a Broadcom driver, then it would be strange.  However if you just read somewhere that your notebook is supposed to use a Broadcom card, then it could just be old documentation.

---

### Post by swornbrother on 2009-01-18
The information I saw about the Broadcom driver, is on their support page for this particular model.  My new install of Vista will not recognize it in the device manager.

I'm beginning to think that HP/Compaq is providing the wrong driver on their support website.

After trying some Atheros windows drivers today, I'll see if that'll get my Vista wireless going.  If it does, I'm going to demand 2 days of my life back from HP (or a managerial position:P).

---

### Post by swornbrother on 2009-01-18
HP/Compaq did indeed screw up.

I talked to a customer service rep, and she confirmed that it is indeed an Atheros chipset in the 215-dx, even though it's specified to be Broadcom on their support page.

If you're trying to get wireless in 32-bit Intrepid on this machine, you can use the Madwifi tutorial located here: 

[http://ubuntuforums.org/showthread.php?t=964836&highlight=atheros](http://ubuntuforums.org/showthread.php?t=964836&highlight=atheros)

64-bit is known NOT to boot on this machine, but the reason is unclear as of yet.

If you're using Jaunty, the wireless should work mostly out of the box.  You just need to deactive support for Atheros wireless in the Hardware Drivers dialog, then restart.

Hopefully this helps anyone who needs it.

---

