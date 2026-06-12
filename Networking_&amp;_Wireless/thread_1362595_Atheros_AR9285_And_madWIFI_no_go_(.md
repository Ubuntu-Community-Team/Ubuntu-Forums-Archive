---
title: "Atheros AR9285 And madWIFI no go :("
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by Cerox Rex on 2009-12-23
Heya, 

I'v tried several times now to install madwifi drivers, but it only winds up mw having no wireless card when i do ifconfig.

lspci says this:

04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)


I'v tried several diffren guides and all winds up with no Wierless interface active.

The Compact wierless drivers seems to work, but they ar kinda unstabal and drops the connection at regular intervalls.

Any help would be apriciatede

---

### Post by gordintoronto on 2009-12-23
Did you look at this thread:
[http://ubuntuforums.org/showthread.php?t=1359723&highlight=AR9285](http://ubuntuforums.org/showthread.php?t=1359723&highlight=AR9285)

It sounds like you don't need madwifi with Karmic.

---

### Post by Cerox Rex on 2009-12-23
Yes i'v tried the steps in that and several other threads here on the forums!

I'm trying to enable my card to run in Monitor mode, but I am unable to, 

When running:
"iwconfig wlan0 mode monitor"  I get no errors but then it resets and shows up in managed mode when i'm doing "iwconfig"

---

