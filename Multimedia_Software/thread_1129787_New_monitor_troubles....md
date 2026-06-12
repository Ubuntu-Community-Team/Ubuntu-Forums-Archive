---
title: "New monitor troubles..."
date: 2009-04-19
forum: Multimedia Software
---

### Post by toejamfootball on 2009-04-19
I just bought a new monitor which tells me it should be set to 1600x900. This isn't an option in the Screen Resolution, is there a way to add it? 

Thanks.

---

### Post by inobe on 2009-04-19
what video card do you have and what driver is installed for it.

---

### Post by toejamfootball on 2009-04-19
> **inobe said:**
> what video card do you have and what driver is installed for it.
Onboard graphics, not sure about driver.```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (CNR) Ethernet Controller (rev 81)
01:09.0 Network controller: RaLink RT2561/RT61 rev B 802.11g

```

---

### Post by inobe on 2009-04-19
you will need to manually edit your xorg.conf

an example only [http://ubuntuforums.org/showthread.php?t=1110275&highlight=resolution+82845G%2FGL](http://ubuntuforums.org/showthread.php?t=1110275&highlight=resolution+82845G%2FGL)[Brookdale

edit: actually that's a bad example, but you will need to add the new line in xorg.

---

### Post by toejamfootball on 2009-04-19
> **inobe said:**
> you will need to manually edit your xorg.conf

an example only [http://ubuntuforums.org/showthread.php?t=1110275&highlight=resolution+82845G%2FGL](http://ubuntuforums.org/showthread.php?t=1110275&highlight=resolution+82845G%2FGL)[Brookdale

edit: actually that's a bad example, but you will need to add the new line in xorg.
Thanks, somehow after I logged out and in again, I was able to select 1600x900. There is a slight movement of angled lines across the screen though, from left to right.

It is hard to see, but noticible enough that it's annoying. Any ideas? Thanks again!

---

### Post by inobe on 2009-04-19
that sounds like antialiasing problems, intel legacy video chipsets are known for this.

---

### Post by toejamfootball on 2009-04-19
> **inobe said:**
> that sounds like antialiasing problems, intel legacy video chipsets are known for this.
Okay, do you know of a solution? Short of getting a new card. I have a spare 64MB card laying around somewhere, could I just put it in and boot?

---

### Post by toejamfootball on 2009-04-19
I installed a different video card, and it is working perfectly now.

Thanks for your help.

---

