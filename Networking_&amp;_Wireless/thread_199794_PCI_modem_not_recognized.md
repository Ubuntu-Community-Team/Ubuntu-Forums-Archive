---
title: "PCI modem not recognized"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by red herring on 2006-06-19
Please help! I have a regular (not winmodem) PCI modem that worked fine in Breezy. It was on /dev/ttyS14. The relevant (I think) output from 'lspci -v' is:

0000:02:02.0 Modem: Agere Systems Venus Modem (V90, 56KFlex) (prog-if 03 [Hayes/16650])
     Subsystem: Agere Systems Venus Modem (V90, 56KFlex)
     Flags: bus master, medium devsel, latency 0. IRQ 169
     Memory at feafec00 (32-bit, non-prefetchable) [size=256]
     I/O ports at d400 [size=256]
     I/O ports at d000 [size=256]
     I/O ports at df00 [size=8]
     Capabilities: [f8] Power Management version 2

Since I upgraded to Dapper, the Gnome networking tool won't auto-detect a modem, and when I tell it to use /dev/ttyS14 (or /dev/ttyS*anything* ) nothing happens.

Thanks

---

### Post by zxee on 2006-06-19
I've had the same experiance with an external modem-going from breezy to dapper.  I don't think the network tool works very well in dapper. Have you tried pppconfig (from a shell)? And in my experiance the only tool that sort of works to connect (besides commandline wvdial & pon) is modem monitor. Hope that helps.

---

### Post by red herring on 2006-06-20
Well I guess I lied -- I never tried /dev/ttyS4, and after reviewing the logs more carefully, that is where the modem is. So now it dials, but two problems remain:

Neither pppconfig nor the gnome tool automatically recognize /dev/ttyS4, which is annoying

and, Netscape doesn't seem to be accepting my username/password anymore, even though I'm paid up! But that's not an Ubuntu problem... Thanks anyway.

---

### Post by zxee on 2006-06-21
> Neither pppconfig nor the gnome tool automatically recognize /dev/ttyS4, which is annoying
Just trying to be helpful-maybe you know this already but you can manually choose ttyS4 as your modem location. Does it still not work when you do that?

---

