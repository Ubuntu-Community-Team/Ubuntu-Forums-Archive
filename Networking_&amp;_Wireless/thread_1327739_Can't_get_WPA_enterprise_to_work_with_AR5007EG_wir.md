---
title: "Can't get WPA enterprise to work with AR5007EG wireless chipset on 9.10"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by Epy on 2009-11-15
I've got a EeePC 1000HA with an Atheros AR5007EG chipset wireless card running vanilla Ubuntu 9.10.

The wireless card will connect to my home router running WPA2/AES, but when I go to school (Ohio State), I can't get it to work with the school's WPA2 enterprise setup.  Our school open source club has outlined how to connect on Ubuntu here: [http://opensource.cse.ohio-state.edu/wireless](http://opensource.cse.ohio-state.edu/wireless).

I've tried many different variations on the default settings: WPA2 enterprise, PEAP version 0, MSCHAPv2, with and without the equifax security certificate, no anonymous identity.  Pretty much tried every variation possible.  I've got several different friends at the open source club running Karmic so I know it's not a school network issue, and I've connected to this network on this laptop within Windows, so I know it's possible.

I've read about an alternate driver for Atheros chipsets, madwifi.  Also read about ndiswrapper.  Has anyone else had trouble connecting to a WPA enterprise network on 9.10?  What are my options here?  Any advice would be appreciated.  Thanks.

---

### Post by Epy on 2009-11-16
Have tried removing ath_pci from the blacklist and then installing the kernel backports package, neither helped.  Is there at least a way to get a more verbose readout when the card can't connect to a network?
 
Anyway, I think now that I've unblacklisted ath_pci I can try to install madwifi again.  When I went to compile it last time it came up with an error almost instantly saying 'no ath_pci.ko file'
 
Again, any suggestions at all?

---

### Post by Epy on 2009-11-16
Problem looking for and found: [http://madwifi-project.org/wiki/About/ath5k/TODO](http://madwifi-project.org/wiki/About/ath5k/TODO)

Blacklisted the ath5k module and am going to try madwifi/ath_pci tomorrow.

---

### Post by Epy on 2009-11-17
madwifi works but not with WPA enterprise and I can't get ndiswrapper to work at all.  Grabbed the infs from a Windows install and ndiswrapper says the hardware isn't present.

---

