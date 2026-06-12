---
title: "Getting wireless to work (Atheros)"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by redb on 2009-04-04
I have just done a clean install of 8.10 on my wifes hp laptop.  My happiness is in the balance.  The laptop has an  Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

The drivers show that it is activated but I cant seem to get it to work.  Any help would be appreciated. 

Thanks

---

### Post by polkadotteapot on 2009-04-04
I've just spent three days on this and got the internet working on my Aao easily using this [http://www.aspireonekernel.com/#Downloads](http://www.aspireonekernel.com/#Downloads)

Then got anything I didn't understand explained her [http://ubuntuforums.org/showthread.php?t=1115748](http://ubuntuforums.org/showthread.php?t=1115748)

Let me know if it works for you.

---

### Post by Bucky Ball on 2009-04-04
Plug an ethernet cable in and grab the updates. It will probably let you know there is a restricted driver ready and waiting for you to use with your card. 

I just did a build for someone and used a card with Atheros and not a problem. Asked me to choose a network and then for my WEP key without me doing much at all. Was up in 5 minutes.

Just make sure you know the name of your router (access point) for when it shows up in 'Available Networks' and the correct security key to join the network.

---

### Post by redb on 2009-04-04
> **Bucky Ball said:**
> Plug an ethernet cable in and grab the updates. It will probably let you know there is a restricted driver ready and waiting for you to use with your card. 

I just did a build for someone and used a card with Atheros and not a problem. Asked me to choose a network and then for my WEP key without me doing much at all. Was up in 5 minutes.

Just make sure you know the name of your router (access point) for when it shows up in 'Available Networks' and the correct security key to join the network.


Here is what or not what is going on.  

If I go to terminal and enter ndiswrapper -l

Nothing comes up??  it just resets back for another command.

Then I run lspci -nn

00:00.0 RAM memory [0500]: nVidia Corporation MCP78S [GeForce 8200] Memory Controller [10de:0754] (rev a2)

00:01.0 ISA bridge [0601]: nVidia Corporation Device [10de:075e] (rev a2)

00:01.1 SMBus [0c05]: nVidia Corporation MCP78S [GeForce 8200] SMBus [10de:0752] (rev a1)

00:01.3 Co-processor [0b40]: nVidia Corporation MCP78S [GeForce 8200] Co-Processor [10de:0753] (rev a2)

00:01.4 RAM memory [0500]: nVidia Corporation MCP78S [GeForce 8200] Memory Controller [10de:0568] (rev a1)

00:02.0 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller [10de:077b] (rev a1)

00:02.1 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller [10de:077c] (rev a1)

00:04.0 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller [10de:077d] (rev a1)

00:04.1 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller [10de:077e] (rev a1)

00:06.0 IDE interface [0101]: nVidia Corporation MCP78S [GeForce 8200] IDE [10de:0759] (rev a1)

00:07.0 Audio device [0403]: nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec [10de:0774] (rev a1)

00:08.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge [10de:075a] (rev a1)

00:09.0 IDE interface [0101]: nVidia Corporation Device [10de:0ad0] (rev a2)

00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP78S [GeForce 8200] Ethernet [10de:0760] (rev a2)

00:0b.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge [10de:0569] (rev a1)

00:14.0 PCI bridge [0604]: nVidia Corporation Device [10de:077a] (rev a1)

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration [1022:1300] (rev 40)

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Address Map [1022:1301]

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h DRAM Controller [1022:1302]

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control [1022:1303]

00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Link Control [1022:1304]

02:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0845] (rev a2)

07:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)

In my hardware drivers it shows that I have support for Atheros  wireless Lan cards and that it is activated and currently in use.

When I set up my other laptop after I downloaded all the updates wireless just popped up and away I went.  

I don't know what I'm doing....:confused:

---

### Post by Bucky Ball on 2009-04-05
Forget ndiswrapper. It is not relevant here. Your card is up. I'm not sure what you have done previously but you may have some kind of conflict if you have ndiswrapper and the regular restricted hardware driver running also.

In System->Administration->Network, have you got the correct details and is configuration set to 'Auto DHCP Config'?

---

### Post by superprash2003 on 2009-04-05
in your terminal type the following commands and post output
1)ifconfig
2)iwconfig
3)iwlist scanning

---

