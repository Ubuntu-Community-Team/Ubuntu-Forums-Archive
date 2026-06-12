---
title: "Slow download speed"
date: 2011-03-15
forum: Networking &amp; Wireless
---

### Post by Lar56 on 2011-03-15
Hi everyone, I am new to Unbuntu, and I recently installed  Lucid Lynx. I noticed that my download speed from the internet is much slower than when I was using Windows. When I installed 10.04 I let the software auto config my network connection. In a previous install of Lucid I did type in all of the addresses and stuff and when the installation finished I had no wireless connection at all. What can I do to get faster downloading? Update drivers?

---

### Post by Tosho on 2011-04-10
I have the same issue on Ubuntu 10.04.2 LTS 64bit.
Wi-Fi and LAN are downloading on the same speed - 1.1MB/s compared to Windows 7 my download for LAN was 6-7 MB/s. And now if I start to download a torrent (even with slow download of 20-100 kb/s) I can't Browse the Internet.

 Adapters:
Intel Corporation Wireless WiFi Link 5100
Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)


any ideas ?

---

### Post by TossTheTV on 2011-04-10
firstly open firefox and type,
about:config
then search: ipv6
and make sure under value it says 'true', if it says false toggle it. 

that should improve your browsing. as far as the network stuff goes, someone else can help you, haven't done it for years. i remember having to set custom "power" values to the wifi adapter and such... 

well before that, one of the easiest things you can do to boost your speed is download ndisgtk in software manager or synaptic. if it doesn't help instantly route the program (will show up under System > Administration > Windows Wireless drivers) to your ethernet card's winxp32bit or win764bit drivers folder, and find the .inf file..
if you don't have those drivers, find them on the company's website (ie Broadcom or Atheros), just like you would have to do if you were running windoze.

---

