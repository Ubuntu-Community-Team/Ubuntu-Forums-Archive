---
title: "Realtek RTL8191SE (draft n)"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by qwerty_uk on 2009-08-07
I got this new Medion E1312 (MD97690) netbook that features the internal wireless card mentioned above. Everything works fine in the pre-installed WinXP SP3

I installed 9.04 via wubi.

The wireless doesn't seem to be supported out-of-the-box, which doesn't surprise me, as it's pretty new. It is listed in lspci, so the system knows it's there.

I've tried (only briefly so far) using ndwrapper and the WinXP driver, but no luck yet. Driver installed ok and didn't cause any crashes, but says it can't detect if the hardware is present (although the window then says that it is!).

Anyway, I'll keep trying to get it working, but what I really want to know is: what is the best way to find out when this card becomes supported natively?

Is the wiki (at [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) ) the most up to date source, or is there any documentation on kernel development that I should check for mentions of the RTL8191SE?

Thanks

---

### Post by memyself on 2009-08-10
Same prob :-( with Medion akoya P6620 with Realtek rtl8191se w-lan 802.11 n Pci-E NIC --- using Ubuntu 9.04 64-bit. ndiswrapper don't work with xp/xp64/vista/vista64 .inf :( :confused:
PLEASE HELP!

THX

---

### Post by maluka on 2009-11-03
I believe you need to install the "Windows 2000 only" driver with ndiswrapper. I'm about to do it on my Toshiba Qosmio x505. I will report back on how it went.

---

### Post by maluka on 2009-11-03
I found [this ]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126")thread that contains a link to a Linux driver that seems to have mixed results.

---

### Post by oprogue on 2010-02-28
Sooo ... now that I'm the owner of a laptop with the RTL8191SE card ... what's the status on this?  Ubuntu supporting this naively yet?

---

### Post by maluka on 2010-03-03
> **oprogue said:**
> Sooo ... now that I'm the owner of a laptop with the RTL8191SE card ... what's the status on this?  Ubuntu supporting this naively yet?

There is a solution. Mine worked for the last few months but an update broke it. I will report back when I find the solution again.

---

