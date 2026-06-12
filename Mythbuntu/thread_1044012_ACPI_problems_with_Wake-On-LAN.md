---
title: "ACPI problems with Wake-On-LAN"
date: 2009-01-19
forum: Mythbuntu
---

### Post by kRiSiS112 on 2009-01-19
Hey all,

I'm having some trouble hooking my backend/frontend box up with wake-on-lan.  I used the guide [here]("http://www.mythtv.org/wiki/ACPI_Wakeup") to set up ACPI on the motherboard to automatically wake up from the internal clock to record shows and shutdown again with mythwelcome on becoming idle.  This uses "mythshutdown --shutdown" to set the clock's wake up time with /sys/class/rtc/rtc0/wakealarm and an ACPI enable setting on the BIOS.

The problem is getting the darn thing to boot back up on command!  Having no wake-on-usb feature in the motherboard to use the remote, I figured my only option is wake-on-lan.

However, shutting down the PC through Linux somehow disables the hardware from accepting the "magic packet."  If I turn on the computer and shut it right back down from POST, WOL works with no problem.  It's once I get into Linux and shut down that it becomes unresponsive.

I've got ethtool-enabled wol support (I think) on each startup from /etc/rc.local with the command:
```
ethtool -s eth0 wol g
```

I don't know if it's relevant but when I use hibernate it has the same effect and when I use standby I can get my PC to wake up from suspension with the remote, but when waking up from either standby or hibernate, the system looks like it's waking but hangs on a black screen.

Much appreciation goes out to the helpful gurus out there who can help. :popcorn:

---

### Post by kRiSiS112 on 2009-01-20
bump! :p

---

### Post by kRiSiS112 on 2009-01-25
Anybody want to take a look at my logs?  I still can't figure this out...

---

### Post by kRiSiS112 on 2009-01-25
Okay, so instead of using my motherboard's built-in NIC, I decided to pop in a PCI card instead.  This thing WORKS now.

SOLVED!

---

### Post by volkswagner on 2009-01-26
> **kRiSiS112 said:**
> Okay, so instead of using my motherboard's built-in NIC, I decided to pop in a PCI card instead.  This thing WORKS now.

SOLVED!

Just curious, is the motherboard proprietary (Dell, Gateway, HP, etc.)?
I have noticed systems like Dell and HP have WOL support, but only from a sleep state, not an off state.

---

### Post by kRiSiS112 on 2009-01-26
The mobo is from FIC (First International Computer).  An obscure mobo to be sure.. I'm running Athlon XP-era hardware for my myth backend and when I had a power surge my last mobo blew out, forcing me to get this one for around $25, lol.

Weird that you mention those top brands don't WOL from off state.  This cheapo brand can handle it.

So yeah, if anyone is reading this and has these problems, go get yourself a NIC card for a few bucks.  Problem solved.  Better yet, get a motherboard that supports wake-on-usb so your remote will work with it!

---

