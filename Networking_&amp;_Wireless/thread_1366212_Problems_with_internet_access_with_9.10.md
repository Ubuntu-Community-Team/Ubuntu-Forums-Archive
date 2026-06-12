---
title: "Problems with internet access with 9.10"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by jackysmith on 2009-12-28
Lots of people having similar problems with 9.10, when 9.04 worked out of the box.
I tried various bits & pieces but once I realised that I could ping servers but not get Firefox to work, I set to trying all the available options in network manager.
Trial and error resulted in this solution for my setup:

Open the network manager by right clicking on the icon in the system tray (top left of screen) and selecting edit connection
Go to the IPv6 tab
Select "LINK-LOCAL ONLY" rather than ignore.
Close the network manager.

You may also need to go to the "IPv4" tab and add your DNS server IP address, if you cant ping an address like "www.debian.com" (use network tools under the system menu).

I'm a real newbie on Linux but using Ubuntu seems a lot easier than windows - the tools work and it seems to be fairly easy to undo mistakes, so my advice would be - keep messing about until you find something that does it!

Jacky

---

### Post by alexfish on 2009-12-28
> **jackysmith said:**
> Lots of people having similar problems with 9.10, when 9.04 worked out of the box.
I tried various bits & pieces but once I realised that I could ping servers but not get Firefox to work, I set to trying all the available options in network manager.
Trial and error resulted in this solution for my setup:

Open the network manager by right clicking on the icon in the system tray (top left of screen) and selecting edit connection
Go to the IPv6 tab
Select "LINK-LOCAL ONLY" rather than ignore.
Close the network manager.

You may also need to go to the "IPv4" tab and add your DNS server IP address, if you cant ping an address like "www.debian.com" (use network tools under the system menu).




I'm a real newbie on Linux but using Ubuntu seems a lot easier than windows - the tools work and it seems to be fairly easy to undo mistakes, so my advice would be - keep messing about until you find something that does it!

Jacky

Hi

What is the network means of access is it mobile broadband or fixed line ect ?

---

### Post by jackysmith on 2009-12-28
It's a wired ethernet, not wireless or mobile.  Thanks.

---

### Post by efflandt on 2009-12-28
Normally if you have supported ethernet and DHCP configured on your router, you do not have to do anything at all to get networking, because an automatic ethernet connection is configured by default.  I set up numerous machines by simply connecting ethernet to a wireless bridge that gets DHCP IP, etc. from my DSL wireless/modem/router.

Although, my old Linksys WET11 wireless bridge seems to be getting a bit flaky, because sometimes it can access the internet at the full 600+KB/sec of my internet connection, but sometimes it stops, and I can access its configuration, but not my DSL modem.  But I also have a Linksys WUSB54GSC that works fine by default, as soon as I configure SSID and wireless security.  I just "ignore" ipv6 because my modem does not do that anyway.

BTW, Ubuntu seems to use much less memory than Win7 Premium just booting up with nothing running.  So when I set up bootable 64-bit Ubuntu 9.10 on a USB drive used for Win7 backup, as a backup OS for someone not Linux aware, I figured I did not need swap w/3 GB RAM.

---

