---
title: "No Sound - Really Need Help"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by StumpyMcDonut on 2008-01-12
Okay, ive got onboard sound with my mobo, and an X-Fi which i cant use for obvious reasons. The onboard is the intel HD Audio, and here is the results of lspci:

00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GS] (rev a1)
04:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
04:04.0 Multimedia audio controller: Creative Labs SB X-Fi
04:05.0 Communication controller: Conexant HSF 56k Data/Fax Modem

Its recognised there, but when i try to use it, i dont have the option to select anything in sound preferences, and i cant open volume control (something about Gstreamer plugins, although i have them installed :?)

Its a real shame cause ubuntu is brilliant, but the lack of sound really ruins it :( ill downgrade to gutsy if thats what is causing the problems, but ive been trying to sort this for ages and am completely stuck

---

### Post by Zimmer on 2008-01-12
Is this your first attempt with Ubuntu/ Linux?

The Hardy Heron 8.01 is still alpha ... not released as complete yet...

If you are trying it out for the first time try an earlier release and maybe a visit to this page
[https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)

will maybe help

---

### Post by StumpyMcDonut on 2008-01-12
Im not exactly a long time user, but im not entirely new. the reason i updated to hardy was because i had an exact same problem with gutsy, although ill downgrade and try again

---

### Post by Zimmer on 2008-01-12
[http://digg.com/linux_unix/Creative_Labs_screws_Linux_users](http://digg.com/linux_unix/Creative_Labs_screws_Linux_users)
is this still relevant?
and this..
[http://www.maximumpc.com/article/where_are_linux_drivers_for_my_x_fi_card](http://www.maximumpc.com/article/where_are_linux_drivers_for_my_x_fi_card)

EDIT:  [http://connect.creativelabs.com/linux/Lists/Driver%20Issues/AllItems.aspx](http://connect.creativelabs.com/linux/Lists/Driver%20Issues/AllItems.aspx)

Info here but it is a bit too much for little old me...

---

### Post by StumpyMcDonut on 2008-01-12
Id gone over all that ages ago - ive given up on creative and have decided not to buy anything from them again ^^

ill reinstall every single sound driver tonight, and if that doesnt work ill downgrade

---

### Post by Zimmer on 2008-01-12
> **StumpyMcDonut said:**
> Id gone over all that ages ago - ive given up on creative and have decided not to buy anything from them again ^^

ill reinstall every single sound driver tonight, and if that doesnt work ill downgrade

Youare not alone, it seems... Vista anyone?

[http://chris.pirillo.com/2006/05/20/huge-creative-x-fi-problems/](http://chris.pirillo.com/2006/05/20/huge-creative-x-fi-problems/)

---

