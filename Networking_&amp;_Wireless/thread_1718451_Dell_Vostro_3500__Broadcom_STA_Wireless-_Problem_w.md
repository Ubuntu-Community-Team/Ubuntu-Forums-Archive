---
title: "Dell Vostro 3500 / Broadcom STA Wireless- Problem with Wired Network"
date: 2011-03-31
forum: Networking &amp; Wireless
---

### Post by robynza on 2011-03-31
Hi, 

Please can someone help. I just got a new laptop...Dell Vostro 3500. Took off Win put on Ubuntu...all went fine. I did all updates and app downloads using my WIRED NETWORK as wireless wasnt working. However I was more interested in setting up the new computer. 

Anyway so after all is installed up pops "Broadcom STA Wireless driver" Proprietary driver do you want to install. Obviously I said yes...

Well now My wireless is working great but for some reason my Wired (auto eth0) no longer works. It just says disconnected and its grayed in.

I'm pretty much a newbie but did try a few things like:

apt-get update
apt-get "something" essential (thats not a command just from memory it was something like that)

However I've had no luck. 

Please can someone help. This Broadcom driver seems to have knocked out my wired network.

---

### Post by robynza on 2011-03-31
By the way im using ubuntu 10.04 LTS

---

### Post by bkratz on 2011-03-31
You might want to check your lspci listing and see if you have a Broadcom device on the ethernet connection too.  If so, you might want to check your blacklist file and see if ssb and b43/b44 were blacklisted during installation of the wireless STA driver.

---

### Post by robynza on 2011-03-31
Hi, 

Thanks for the reply. Im not really sure how to do that. 

My output is the following:

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
12:00.0 Network controller: Broadcom Corporation Device 4353 (rev 01)
13:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)


Does that help anything? Sorry...still a newbie. 

Thanks

---

### Post by bkratz on 2011-03-31
Yes, it does,

[COLOR="Red"]Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
[/COLOR]

 nevermind--but I will continue to take a look.

---

