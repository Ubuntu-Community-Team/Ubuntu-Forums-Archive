---
title: "No wireless connection whatsoever?"
date: 2012-07-29
forum: Networking &amp; Wireless
---

### Post by Phubu on 2012-07-29
Hi,

I just installed Ubuntu 12.04 LTS as a 2nd OS to dual boot into. The problem is i have no wireless connection at all, nothing shows up. I have tried everything possible like ndisgtk to install the .inf file that went ok but still nothing happened... Also followed tons of suggestions on the internet and nothing.

I have a Dell Optiplex 755, with a Trendnet TEW643PI., Dualbooting with Win7.

I will appreciate any help if possible, I've always like Ubuntu, but trying to solve things like this just drives people insane and away from the OS lol.

---

### Post by carl4926 on 2012-07-29
```
sudo lspci -nnk | grep -iA2 net
```

post result

---

### Post by Phubu on 2012-07-29
Here is the output:

> 00:19.0 Ethernet controller [0200]: Intel Corporation 82566DM-2 Gigabit Network Connection [8086:10bd] (rev 02)
	Subsystem: Dell OptiPlex 755 [1028:0211]
	Kernel driver in use: e1000e
--
03:02.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8190 802.11n Wireless LAN [10ec:8190]
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8190 802.11n Wireless LAN [10ec:8190]



---

### Post by carl4926 on 2012-07-29
Yuck

[http://ubuntuforums.org/showthread.php?t=1569834&highlight=RTL8190](http://ubuntuforums.org/showthread.php?t=1569834&highlight=RTL8190)

---

### Post by Phubu on 2012-07-29
that sucks, i had already ran into that post today but the guy doesnt even prove it worked by showing, hes just saying it worked and gives the links to email addresses.

---

### Post by carl4926 on 2012-07-29
Yep.
Most of their devices work OOTB.

If it were me, I'd probably put a cheap USB wireless dongle in. Or pull your current PCI device and replace.

These work well
tenda-wireless-n150-usb-adapter-w311u

---

### Post by Phubu on 2012-07-29
> **carl4926 said:**
> Yep.
Most of their devices work OOTB.

If it were me, I'd probably put a cheap USB wireless dongle in. Or pull your current PCI device and replace.

These work well
tenda-wireless-n150-usb-adapter-w311u

i guess i can check those out.

---

### Post by ajvzomeren on 2012-07-29
> **Phubu said:**
> i guess i can check those out.

An Linksys WUSB54GC is also a good adapter and in my case working with ALL Ubuntu versions.
Working out of the box!
Success

---

### Post by Phubu on 2012-07-29
I was wondering if this one works since its pretty cheap:

Netgear WNA3100 N300
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=607838&CatId=2704]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=607838&CatId=2704")

Edit: 
Never mind didnt it even see it here:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

Edit:I just bought... Netgear WN111v.2 2.0 USB works (Plug & Play)

---

