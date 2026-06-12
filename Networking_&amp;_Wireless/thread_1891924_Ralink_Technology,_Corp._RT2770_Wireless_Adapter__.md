---
title: "Ralink Technology, Corp. RT2770 Wireless Adapter // Ubuntu 11.04 // 32bit AMD Athlon"
date: 2011-12-06
forum: Networking &amp; Wireless
---

### Post by aislaith on 2011-12-06
I just installed Ubuntu 11.04 and my wifi almost worked! It registers the USB wireless adapter and picks up my network and asks for a WPA key, but it wont connect. At first i was able to use the network manager tool in the terminal and the state was connecting, but the only thing wrong that i could see was that link=no. Whereas now typing commands in the terminal seems to just freeze up and the cursor just blinks at me...??

Machine Brand: AMD Athlon 32bit Home Built Desktop
Wireless Brand: NetComm NP900n
                Ralink Technology, Corp. RT2770 Wireless Adapter
iwconfig didnt work
lsmod didnt work either
Kernel Boot Messages: phy0 &#8594; rt2x00usb_vendor_request: Error – Vendor Request 0x07 failed for offset 0x1004 with error
Network Configuration: this command worked for me in the past, but i don't remember what it said, it doesnt want to work for me now
Ubuntu Version: -110
Ubuntu 11.04
2.6.38-8-generic i686

I have some programming education, 1st year University in Computer Science, but that was a few years ago, and it was in Java, and its is most certainly not helping me much! What can i read to find out more about my problem? Can you briefly explain to me what my problem is? Or can you summarise what the solution might be? Thanks, Ais

---

### Post by praseodym on 2011-12-07
Hi,

please show the outputs of:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```
I recommend updating your system first via cable connection, if possible. Kernel -8 is the default installation one.

Edit: Are the wireless-tools installed?

```
sudo apt-get install wireless-tools
```

---

### Post by aislaith on 2011-12-07
> **praseodym said:**
> Hi,

please show the outputs of:

```

lsmod
iwconfig

```

I recommend updating your system first via cable connection, if possible.]

Like i said,
```

lsmod
iwconfig
```
don't work in the terminal. It just does nothing. The cursor just moves to the next line and blinks. When i first booted it, the terminal was working fine, but once i opened Windows 7 on my other partition to access the internet and this forum, then rebooted ubuntu again, it no longer worked.

And i would very much like to connect via a ethernet as well, and i did think of that, but its not practical.

---

### Post by praseodym on 2011-12-07
Can you show the outputs using a Live-CD? Does "apt-get" work with cable?

---

### Post by aislaith on 2011-12-13
yep thanks. i bought an ethernet cable, moved my desktop onto the dining room table, hung cords all over the place and updated no worries at all. now my usb wireless adapter works like a charm. 

thanks.

---

