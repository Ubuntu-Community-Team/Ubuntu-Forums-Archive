---
title: "What Wireless LAN cards &quot;just work&quot;?"
date: 2006-04-26
forum: Networking &amp; Wireless
---

### Post by hanakj on 2006-04-26
I am having a devil of a time getting my D-Link DWL-650+ to work.  I have basically given up.  I am tired of messing around with the stuff in the acx100 site and trying to get ndiswrapper to work.  Windows just recognizes it.  Ubuntu doesnot.  ](*,)   What decent(but not too pricey) WLAN cards "just work"?

---

### Post by mjm115 on 2006-04-26
Here's a good start:

[http://www.ubuntuforums.org/showthread.php?t=128389](http://www.ubuntuforums.org/showthread.php?t=128389)

Also:

[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

---

### Post by mjwood0 on 2006-04-26
I have a Senao 2511 which works with the wlan drivers as well as the hostap drivers.

I also have a Cisco Aironet 350 which works out of the box. 

Of the two, the Cisco was less of a problem since I didn't need to install drivers.

---

### Post by plexi50 on 2006-04-26
I have an old Belkin B card that works everytime, detected on install, just enter the WEP key, also just bought a cheap Airlink/Atheros based super G card @ Fry's for 14.99 that worked out of the box with network manager.
 
I am using Breezy with no wrapper, so the kernel is doing all the drivers

---

### Post by celem on 2006-04-26
I have used two WiFi PCMCIA cards on Ubuntu 5.10 with my DELL Latitude C400 laptop. The first, a Wistron NeWeb WLAN b Cardbus Adapter CB200B from Wistron Neweb Corporation, worked very will with ndiswrapper. However, to answer your question, my AVAYA Wireless GOLD WorldCard "Just Works". When I plugged it in, Ubuntu invoked the orinoco driver and it works, every time. There is one thing that annoys me, however. The RFMon feature isn't supported by the Ubuntu installed driver and thus it won't "sniff" to see what networks are present and let me select one, as it does with Windows. There are driver patches that correct this issue ([http://airsnort.shmoo.com/orinocoinfo.html)](http://airsnort.shmoo.com/orinocoinfo.html)). I certainly wish that the Ubuntu drivers incorporated these fixes. Anyway, so long as you know the SSID and WEP key in advance, it works "out of the box"

---

### Post by steve.horsley on 2006-04-26
As far as I can tell, this works perfectly in Dapper: 
Foxconn WLL-3350
My base station is only 11Meg so I haven't tried the 54 meg, but I have no reason to doubt it. The great thing is the out-of-the-box support - no messing with ndiswrapper at all.

[http://www.newegg.com/Product/Produc...82E16833194001](http://www.newegg.com/Product/Produc...82E16833194001)

---

### Post by Pimpity Snicket on 2006-04-26
[QUOTE=plexi50]I have an old Belkin B card that works everytime, detected on install, just enter the WEP key, also just bought a cheap Airlink/Atheros based super G card @ Fry's for 14.99 that worked out of the box with network manager.
 
I am using Breezy with no wrapper, so the kernel is doing all the drivers[/QUOTE]

I see those deals every day cause I follow the newspaper ads online religiously.  I'm having a hell of a time w/ my card so I'm considering getting an airlink since they have 802.11g pci cards for like $10.  They don't list any model numbers online so I've been lookin around for experiences, glad to see yours worked out of the box.

---

### Post by hanakj on 2006-04-27
Thanks folks!  You've given me a lot of info.  I'll get cracking!

---

### Post by celem on 2006-04-30
[QUOTE=celem]I have used two WiFi PCMCIA cards on Ubuntu 5.10 with my DELL Latitude C400 laptop. The first, a Wistron NeWeb WLAN b Cardbus Adapter CB200B from Wistron Neweb Corporation, worked very will with ndiswrapper. However, to answer your question, my AVAYA Wireless GOLD WorldCard "Just Works". When I plugged it in, Ubuntu invoked the orinoco driver and it works, every time. There is one thing that annoys me, however. The RFMon feature isn't supported by the Ubuntu installed driver and thus it won't "sniff" to see what networks are present and let me select one, as it does with Windows. There are driver patches that correct this issue ([http://airsnort.shmoo.com/orinocoinfo.html)](http://airsnort.shmoo.com/orinocoinfo.html)). I certainly wish that the Ubuntu drivers incorporated these fixes. Anyway, so long as you know the SSID and WEP key in advance, it works "out of the box"[/QUOTE]
My CB200B was last used with ndiswrapper on Breezy. Since I upgraded to Dapper I had not tried it, assuming that ndiswrapper would still be needed. Well, I read a posting that said that Dapper now supports rtl8180 directly, so I decided to simply plug in the CB200B and see if native support work. WOW - yes it does! and better than the orinoco card. My cheap $10 Wistron NeWeb WLAN b Cardbus Adapter CB200B, from Wistron Neweb Corporation, PCMCIA WiFi card that I purchased off of eBay works great and RFMON must be working because it now finds and notifies me of the networks that it sees - something that the orinoco card fails to do.:-D

---

### Post by kmoffat on 2006-04-30
I have a Netgear 511 (pcmcia card) which is based on the prism54 driver, and works fine with ubuntu 5.10. I got it reconditioned quite cheap from buy.com. I think the newer Netgears use a different chipset than the prism54, but I'm not sure about that. Anyway, it works in both ubuntu and kanotix without wrapper.

---

### Post by celem on 2006-07-25
For my Dell C400, I purchased on eBay, an Intel 2100 MiniPCI Wifi card (Dell P/N 0U2027) and installed it in my C400 today. I read the installation instructions on the Dell site and when I discovered that ALL C400s have the antenna wires inside, even if ordered without the internal WiFi, I ordered the MiniPCi WiFi card.  After the installation (easy with the DELL instructions), I powered up Dapper 6.06 and it instantly recognized the card and it "just works". I am a happy camper now - no more external card sticking out of my C400.

---

