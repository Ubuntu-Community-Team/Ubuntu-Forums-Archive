---
title: "Using both Wireless and Cable"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by mrkazoodle on 2010-05-03
Hi

I normally use a cable to connect to the Internet, but I also use the wireless network regularly.
So I'd like Ubuntu to automatically use the wired connection except when there isn't any.

I also have the unlock keyring problem (because of auto login and wireless Internet), does anyone know a solution to that problem? [SIZE="1"](It's quite disturbing to get that window each time you start the pc even if you aren't going to use wireless Internet)[/SIZE]

system:
Ubuntu 10.04, auto login, Intel Core 2 Quad Mobile Q9000, ATI HD 4670, 4 GB RAM, Broadcom NetLink BCM5784M Gigabit Ethernet PCIe, Intel Wireless WiFi Link 5100

---

### Post by andreseso on 2010-05-13
I just installed a Wifi dongle that works correctly, but it uninstalled my wired connection.  I am able to navigate through Internet correctly but as my wired eth0 interface is disabled, I cannot reach my Network printer.

Is there any way to have both wireless and wired enabled at the same time?  I am using Lucid.

Love,
Andres

---

### Post by andreseso on 2010-05-15
My usb wifi dongle disabled my wired connection.  How do I get my wired connection back while still using wifi?

Love,
Andres

---

### Post by Ginsu543 on 2010-05-15
Check out _[this]("http://ubuntuforums.org/showthread.php?t=1093770")_ thread. Netztier's post #6 in particular should be helpful. The key is to use a static IP address for the wired.

---

### Post by lisati on 2010-05-15
Moved to "Networking & Wireless"

---

### Post by andreseso on 2010-06-08
> **Ginsu543 said:**
> Check out _[this]("http://ubuntuforums.org/showthread.php?t=1093770")_ thread. Netztier's post #6 in particular should be helpful. The key is to use a static IP address for the wired.

OK,

I have eth0 with a static IP address.  I have wlan0 with a DHCP address.  Both have the same subnet.  Previous attempts the default route went through eth0 which is not connected to the router.  I could print but to surf, I had to disable eth0.

Right clicking NM I configured eth0's gateway to be 0.0.0.0.   After reboot, route -n showed the default gateway to be wlan0 to the router.  The NM symbol was the wireless symbol. However I could neither surf nor print.  I had to disable eth0 to surf.

I want to use eth0 for printing and wlan0 for surfing.  Right now they do not access the same parts of the network as I am having problems with my Internet connection so the router is connected directly to the entry of the phone line.

Any help would be appreciated.

Love,
Andres

---

### Post by andreseso on 2010-09-01
I have Network hell.  I have tried installing USB dongle on my vista computer and it fails.  On my 10.4 computer (Lucid Lynx?) I have a working USB dongle but I have to disable wired access to surf Internet.  With wired connection to the router Chromium displays web pages but Firefox does not.  To print when the router is connected only to the phone line entrance of my home (in spain it is called ptr) i have to disable wireless and enable wired to print to my wired printer.

at least now xsane is able to use my wired printer as a scanner.

love,
andres

---

