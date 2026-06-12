---
title: "internet connection drops suddenly"
date: 2010-05-26
forum: Networking &amp; Wireless
---

### Post by khoacao on 2010-05-26
I have quite a problem with my internet connection recently. It just drops without any reason. I tried to ping and it gave me no response.
This is what I have been doing so far to get it fixed, temporarily it seems:
[INDENT] I unplugged the router and modem, plugged back in after some minutes, then everything working fine for some time before dropping significantly, and this happens to my wired computer, if not wireless, which is worse. Let say, I plugged in, and started downloading, the speed would reach 2.2mbps, and then would drop to ~220kbps after some time, then some hours later, the whole connection would come to a halt even though it still said "connected" when I checked for network connection. 
[/INDENT]Does anyone have any idea what is going on with my connection?

Thank you much in advance

---

### Post by shebaw on 2010-05-27
What version of Ubuntu are you using?
And post type this in the terminal and paste the results > lspci

---

### Post by dobelden on 2010-05-27
i have same problem, after receck on my network, thereis IP address have staticly configuration on my server, if my dhcp client get that IP, my pc cant access to internet.

---

### Post by khoacao on 2010-05-27
> **shebaw said:**
> What version of Ubuntu are you using?
And post type this in the terminal and paste the results

This is where the internet is acting "NORMAL"

khoacao@khoacao-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82Q963/Q965 Memory Controller Hub (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 01)
00:03.0 Communication controller: Intel Corporation 82Q963/Q965 HECI Controller (rev 01)
00:03.2 IDE interface: Intel Corporation 82Q963/Q965 PT IDER Controller (rev 01)
00:03.3 Serial controller: Intel Corporation 82Q963/Q965 KT Controller (rev 01)
00:19.0 Ethernet controller: Intel Corporation 82566DM Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HO (ICH8DO) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)

---

### Post by khoacao on 2010-05-29
> **shebaw said:**
> What version of Ubuntu are you using?
And post type this in the terminal and paste the results

AND THIS IS WHERE THE WHOLE THING IS ACTING WEIRD

khoacao@khoacao-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82Q963/Q965 Memory Controller Hub (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 01)
00:03.0 Communication controller: Intel Corporation 82Q963/Q965 HECI Controller (rev 01)
00:03.2 IDE interface: Intel Corporation 82Q963/Q965 PT IDER Controller (rev 01)
00:03.3 Serial controller: Intel Corporation 82Q963/Q965 KT Controller (rev 01)
00:19.0 Ethernet controller: Intel Corporation 82566DM Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HO (ICH8DO) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)

---

### Post by mcbond1010 on 2010-05-29
I have the exact same issue.  Connection starts strong and eventually degrades to nothing. Hope somebody knows the solution :(

---

### Post by khoacao on 2010-06-01
I have also been told that due to many wireless devices in the house, the signal could be corrupted or interfered, therefore, I tried to limit the usage of those devices for a day, and used only the wired connection in my desktop. I left my torrents over night, then checked back the following morning, well, guess what, the internet connection was dead for no reason. I was thinking it was due to bad cable connectors. However, I noticed that when I downgraded my Cox service from Premium to Preferred, this problem happened more frequently than it had been before. So it is really frustrating, either of the services does me no good, i still got drops for no reason. Any thoughts? It could be my modem and router??

---

