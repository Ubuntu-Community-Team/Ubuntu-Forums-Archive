---
title: "Wireless/ethernet networking with ubuntu 8.04 and vista"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by BardSeed on 2009-11-13
I apologise if you're tired of seeing threads like this; I don't currently have the internet at home so I have little time to search around.

I have a desktop running ubuntu 8.04 that is connected to my router via an ethernet cable. It can't detect the router wirelessly and I'd rather not buy a dongle. I want to network with a laptop running Windows vista. The laptop can connect to my router wirelessly, but I don't know how to go about sharing files.

I've read something about samba and having to adjust the settings in Windows, but I don't have samba installed on my desktop. I suppose I could download it on the laptop and pass it across with a USB stick, though.

I have absolutely no clue about networking, so please bare this in mind if you have an answer for me. Help will be much appreciated.

---

### Post by Iowan on 2009-11-13
So, you've got a couple of things that need to happen. First, connect both machines to the router and check their IP addresses From a terminal (Applications>Accessories>Terminal) type **ifconfig -a**. I'd need to fire up my laptop into Vista to discover how to learn it's IP address - especially via wireless.

The next task will be to install Samba on Ubuntu if you intend to share files to Vista from it. [Here]("http://ubuntuforums.org/showthread.php?t=202605") is a How-To, and a [help page]("https://help.ubuntu.com/community/SettingUpSamba").

---

