---
title: "Pleased my Air Card works, but..."
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by sledjockey on 2009-04-03
For whatever reason, I can't get my system to connect to any wireless with WEP or WPA, nor any vpns....  

I swapped from Suse to Ubuntu in hopes that my VZW Air Card would start working.  It did and quite easily, I might add.....  The install process seems a bit easier with Unbuntu as well.  There seem to be less "anomalies" than Suse.

However I will also add the following things that suddenly don't work with Ubuntu to include the previously listed.  This way it is an all inclusive list:

Citrix ICA Client
VPN (Cisco and PPTP)
Wireless if WEP or WPA is used (common with my wife's and daughter's Ubuntu installs as well)

Any assistance would be greatly appreciated.

---

### Post by sledjockey on 2009-04-03
Forgot to post:

Ubuntu 8.10
Compaq Presario v2000

Wife's:
Dell Mini 9"
Ubuntu 8.04

Daughter's:
Dell Inspiron 1525 (or whatever comes with Ubuntu)
Ubuntu 8.04

Thanks

---

### Post by coffeecat on 2009-04-03
Am I reading you right? Are you saying that your wife's and daughter's Dells came with Ubuntu preloaded by Dell, and that they won't connect with WPA or WEP either? If that's the case, then look at your router or router settings first. Dell don't sell machines that can't connect to encrypted wireless networks - of that I am sure.

---

### Post by sledjockey on 2009-04-03
You are reading this correctly.....  Neither of the Dells will connect to the wireless either.

I have tried a Linksys WRT54G, a Belkin (POS), and Netgear WNR834B and some netgear business class one that we use at work that I can't remember the model of.

All will allow Windows connections, the Ubuntu can see the network, but it won't connect if a password is required.  Even my openSuse had no problems and it also used NetworkManager, so I am familiar with the program.  It just doesn't connect with the Ubuntu....

It is actually beginning to become irritating.

---

### Post by coffeecat on 2009-04-04
> **sledjockey said:**
> It is actually beginning to become irritating.

I sympathise with you.

I'm sorry I have nothing really contructive to offer, except to say that my experience of both 8.04 and 8.10 is that, so long as you are using a compatible wireless card, connecting wirelessly (using WPA and WPA2) is actually easier (and more reliable) than with Windows.

By replying I've bumped your post for you, so hopefully someone else might have something useful to offer. In the meantime, why not post the terminal output of 'lspci' from the machine with the VZW Air Card, to see what the chipset of that particualr device is?

---

### Post by sledjockey on 2009-04-04
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
05:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

---

### Post by sledjockey on 2009-04-06
Bump...

Getting ready to through Tomato on the Linksys and see if it is some weird thing with the new routers.  At least the Tomato is Linux based and will be accepting of a Linux box at that point...  Hopefully.

---

### Post by coffeecat on 2009-04-06
This is the relevant line from lspci:

> **sledjockey said:**
> 05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I have absolutely no experience of Broadcomm wireless, but from various threads I've seen, I gather that Broadcomm is not the best choice of wireless chipset to have. Sorry. Suggest you search the forum for BCM4318 and see what you come up with. Also, [this link]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") might be of help.

Or perhaps someone with Broadcomm experience might join the thread.

---

