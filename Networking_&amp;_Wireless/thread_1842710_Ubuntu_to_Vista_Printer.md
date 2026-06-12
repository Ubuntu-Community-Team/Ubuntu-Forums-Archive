---
title: "Ubuntu to Vista Printer"
date: 2011-09-12
forum: Networking &amp; Wireless
---

### Post by ttoolin on 2011-09-12
Hi-

My home network collapsed on its own, a few weeks ago.  I don't know why, but since I had to open ports on my Vista McAfee Firewall, in order to restore file sharing, I suspect that an automatic software update, to that, had a major part of it. I really don't know, though.

I have restored file sharing, and it works well.  I am not able to restore printer sharing, despite the fact that it worked fine, a few weeks ago.

Help and advice would be much appreciated.

I am running lucid netbook remix, with Samba, CUPS and HPLIP installed.  My printer is an HP laserjet 1000 on a Win Vista machine.  The ubuntu  printer setup utility recognizes the printer across the network, and allows me to install the driver, then fails when I attempt to print a test page.  The Vista box does not show any indication that a print attempt has taken place.

I have opened port 631 on the Vista Firewall.  There is one other problem that may be a contributing factor:  When I had the same printer installed locally on the ubuntu netbook, I needed to download an updated driver.  I unsuccessfully attempted to do so with hp-setup, from a terminal window, but that program will not proceed without finding the printer, and I cannot get it to discover it.  The Vista machine has its own driver for the printer, if there is a way to feed it data in a raw form.

I have unloaded and reinstalled SAMBA, CUPS and HPLIP software, during my attempts to fix this.  Although I tried it, I'm not using Samba version 4.  It say's it's experimental, and it doesn't have the ubuntu icon along with it, in synaptic.

It was working fine, a few weeks ago.  I did not actively do anything to change that, it appears to be a software update that caused the dilemma.

Thanks, in advance, for the help!

Terry

---

