---
title: "Cannot connect to WPA2 secured networks after 10.10 upgrade."
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by Frostshock on 2010-10-13
Unsecured and WEP networks are fine. I do not have a WPA network to test on, but my school's WPA2 Eduroam network does not work. It tries to connect before asking again for my credentials, and this repeats.

I'm on 64-bit 10.10 Ubuntu upgraded from a live CD install of 10.04.

Laptop model is Acer Aspire 5741-5193. Output of lspci:

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
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
02:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

Thanks in advance.

---

### Post by jarv on 2010-10-13
Also experiencing the same issue after upgrading to 10.10 for WPA2 authentication.

in syslog i'm seeing the following errors from wpa_supplicant
"Association request to the driver failed"
"WPA: Failed to get master session key from EAPOL state machines"
"WPA: Key handsake aborted"

(BCM4312)

---

### Post by Frostshock on 2010-10-14
It appears that it works when I choose to load Linux 2.6.32-25-generic instead of Linux 2.6.35-22-generic. Well, works better anyway, sometimes our school network is a bit shoddy and won't connect with any operating system, but I can connect with the older version of Linux compared to never connecting with the new one. I tested them back to back when I knew for a fact the network was working and the older version worked 100% of the time and the new version never connected once.

---

### Post by CedricMC on 2010-10-14
The bug and a workaround have been submitted to the developers [here]("https://bugzilla.gnome.org/show_bug.cgi?id=632184").

---

### Post by julianof on 2010-10-20
Any news on this?

I am having the same issue...

Thanks!

---

### Post by bigfootnmd on 2010-10-20
Other posts in the forum indicate a possible issue with WPA using TKIP.  If you are using TKIP encryption try switching to AES.

---

### Post by julianof on 2010-10-20
> **bigfootnmd said:**
> Other posts in the forum indicate a possible issue with WPA using TKIP.  If you are using TKIP encryption try switching to AES.

The problem is that I cannot play with the router to change the encryption method since I am not the network administrator.

Thanks anyway!

---

### Post by darth62969 on 2010-10-20
> **bigfootnmd said:**
> Other posts in the forum indicate a possible issue with WPA using TKIP.  If you are using TKIP encryption try switching to AES.
useing that and it works just fine... had a issue but it turned out to be a wireless disabled type thing. (check the [B][ubuntu netbook remix] Ubuntu 10.10 Wireless Really Flaky thread for more info) [http://ubuntuforums.org/showthread.php?p=10002224#post10002224](http://ubuntuforums.org/showthread.php?p=10002224#post10002224)
[/B]

---

### Post by Spoone on 2011-02-03
So what if you don't even have the option of switching to AES?
I have a fresh install of 10.10, and while my network is seen, it cannot be reached.  Neither TKIP nor  AES is simply not an option given when trying to connect.

---

### Post by lordadi on 2011-02-16
Apparently WPAsupplicant is "bad" under 10.10 for Eduroam - I used [this]("http://twitter.com/RyanFox/status/27909423330492419") and my T400 would at least connect to Eduroam and work for the most part.

Every now and then it get's all confused and can't be used, you need to restart in such cases.

---

### Post by cswetenham on 2012-01-17
> **lordadi said:**
> Apparently WPAsupplicant is "bad" under 10.10 for Eduroam - I used [this]("http://twitter.com/RyanFox/status/27909423330492419") and my T400 would at least connect to Eduroam and work for the most part.

Every now and then it get's all confused and can't be used, you need to restart in such cases.

The page that twitter post links to is now a 404, and archive.org doesn't have a copy.

I am having trouble connecting to eduroam on 11.04.

---

