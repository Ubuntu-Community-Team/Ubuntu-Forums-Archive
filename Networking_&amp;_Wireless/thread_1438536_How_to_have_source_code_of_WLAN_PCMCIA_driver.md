---
title: "How to have source code of WLAN PCMCIA driver?"
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by pepros on 2010-03-25
Hi all,

I am a newbie on Ubuntu. I intend to attach WLAN PCMCIA card to my embedded system to connect to a wireless network. However, my embedded system uses a strangs OS that not supports the card driver. I think that I can investigate on how Ubuntu control the card to find out the way to control it in my system. The WLAN PCMCIA card that I can buy is:
TP-Link TL-WN510G,
Linksys WPC54GS

Can any one tell me, how can I have the source code of WLAN PCMCIA driver and how can I find out the way Ubuntu control this card?

Thanks.

---

### Post by superfrogman94 on 2010-03-25
unless the driver is open source you wont be able to get the source code. did you try going to hardware drivers and seeing if a  propetiery driver is available? Thats located at System -> Administration -> Hardware Drivers. try displaying the output if these commands:
```
lshw
```  ```
lspci
``` you could also try using the windows driver in ndiswrapper.

---

### Post by pepros on 2010-03-26
Thank you very much for your advise.
When I go to System->Administration->Hardware Drivers, the system suggests to activate the "madwifi". So how can I find out the way that madwifi control the PCMCIA card.

---

### Post by chili555 on 2010-03-26
This might be it: [http://madwifi-project.org/browser/madwifi/trunk](http://madwifi-project.org/browser/madwifi/trunk)

---

### Post by pepros on 2010-03-31
I have tried to make the card run on Ubuntu, and finally, it runs normally with ath5k driver. As I know, this driver is the later generation of madwifi, right? However, I can not realize the existence of ath5k source code in the madwifi project site.

---

