---
title: "Ubuntu 10.04 - Exclamation point (!) next to wireless icon"
date: 2010-07-21
forum: Networking &amp; Wireless
---

### Post by Alvina on 2010-07-21
Hi all.

There's an exclamation point next to my wireless icon up at the top which concerns me.  I've just installed Ubuntu 10.04 yesterday - absolutely love it.

The only problem is that I'm having trouble with staying connected to my wireless network...

When it is connected, there is an exclamation point next to the wireless icon.

I have Broadband internet, Belkin N Wireless router, and an Acer Aspire 5741 with the wireless device built into the laptop.

This normally runs fine with Windows 7, but it doesn't automatically connect with Ubuntu 10.04...

How can I fix this?  Any ideas would be greatly appreciated. 

Thanks in advance!
(I attached a screen shot of the icon below.)

---

### Post by dca on 2010-07-21
Your laptop indicates it has an *Acer InviLink™ Nplify™ 802.11b/g/n Wi-Fi CERTIFIED* card or InviLink b/g card.  Without knowing the chipset, it's stuff to say if Ubuntu is even compatible w/ that card.  Try typing **sudo lspci | grep -i "wireless"** in Terminal and posting back response...  If it displays nothing swap out wireless with wifi between the quotes...

---

### Post by dca on 2010-07-21
...does this sound like what you're running into?
 
[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/118409](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/118409)
 
...also try removing the wireless network completely in network manager and re-adding it...

---

### Post by Alvina on 2010-07-21
> **dca said:**
> ...does this sound like what you're running into?
 
[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/118409](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/118409)
 
...also try removing the wireless network completely in network manager and re-adding it...


Yes! That sounds exactly like my problem! lol

---

### Post by Alvina on 2010-07-21
> **dca said:**
> Your laptop indicates it has an *Acer InviLink™ Nplify™ 802.11b/g/n Wi-Fi CERTIFIED* card or InviLink b/g card.  Without knowing the chipset, it's stuff to say if Ubuntu is even compatible w/ that card.  Try typing **sudo lspci | grep -i "wireless"** in Terminal and posting back response...  If it displays nothing swap out wireless with wifi between the quotes...

Okay, so I typed in **sudo lspci **in the Terminal and this is what it gave me:
[INDENT]00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
02:00.0 Network controller: Broadcom Corporation Device 4357 (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
[/INDENT]**grep -i "wireless" **and** grep -i "wifi" **gave me nothing.

---

### Post by corncob on 2010-07-21
> **dca said:**
> ...does this sound like what you're running into?
 
[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/118409](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/118409)
 
...also try removing the wireless network completely in network manager and re-adding it...

I had just installed 64 bit 10.04 on my HP dv6835nr notebook yesterday and had the same problem and it just wouldn't connect at all wirelessly.  When I got it out today so I could follow the instructions on that link, everything was working.  I guess it just needed a hard reboot.  I had it unplugged but didn't go to the extent of taking the battery out.

---

### Post by Alvina on 2010-07-21
> **corncob said:**
> I had just installed 64 bit 10.04 on my HP dv6835nr notebook yesterday and had the same problem and it just wouldn't connect at all wirelessly.  When I got it out today so I could follow the instructions on that link, everything was working.  I guess it just needed a hard reboot.  I had it unplugged but didn't go to the extent of taking the battery out.


Okay, thanks for sharing that with me.  I'll have to try that a little later.  

...That line written in your signature made me laugh. :-)

---

### Post by networkslave on 2010-07-21
Hey Alvina

Do you have normal network access or do you have trouble accessing the network?

Check your network config by right-click on the network link-icon and selecting 'connection information'
Do you have a DNS server assigned?

I have had this happening that the wireless AP does not assign the DNS but it does assign the IP and Gateway.  When that happens, I have that Exclamation mark.

---

### Post by Alvina on 2010-07-21
> **networkslave said:**
> Hey Alvina

Do you have normal network access or do you have trouble accessing the network?

Check your network config by right-click on the network link-icon and selecting 'connection information'
Do you have a DNS server assigned?


Accessing the network is normal for me.  I can connect to the wireless network but when I do, that exclamation point comes up and under "Wireless Network," it doesn't say I'm connected when I am. 

Yes, I think I have a DNS server assigned... When I go to 192.168.2.1, it shows a DNS address.

---

### Post by Nandro3 on 2010-07-24
I have this same problem as well and have just removed network-manager and replaced it with with till its fixed or I an locate a work around

---

### Post by Qboy61 on 2010-09-25
I have the same exclamation point when using Ubuntu 10.01 32-bit and HP Mini 5102 with Broadcom WiFi.  Icon shows connection correctly on 2.4GHz (802.11g) but not correctly on 5.2GHz (802.11a).

---

### Post by kev196 on 2011-09-27
i also have problems can some 1 help ! sybol on my wireless and dosent connect to anything or finds any networks but it use to work when i first got ubuntu 11.04

---

### Post by corncob on 2011-09-28
> **kev196 said:**
> i also have problems can some 1 help ! sybol on my wireless and dosent connect to anything or finds any networks but it use to work when i first got ubuntu 11.04

Welcome to the forums!  Try a hard reboot.  Unplug the router and modem, and turn off the computer (take the battery out if its a laptop).  Then, after a few minutes, start everything up again.

---

