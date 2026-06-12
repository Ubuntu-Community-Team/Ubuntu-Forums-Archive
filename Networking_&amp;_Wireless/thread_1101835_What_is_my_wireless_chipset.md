---
title: "What is my wireless chipset?"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by kumoshk on 2009-03-20
sudo lshw gives me this output for my card:

        *-network:1 UNCLAIMED
             description: Network controller
             product: RaLink
             vendor: RaLink
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=32 maxlatency=4 mingnt=2

I need to figure out what the chipset is, but it doesn't say here. Is the card not installed physically, properly?

Here's a link to the card I got:
[http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=4389486&csid=ITD&body=MAIN#detailspecs](http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=4389486&csid=ITD&body=MAIN#detailspecs)

Note that when I received it, Sabrent wasn't the brand (although the card appeared the same otherwise). The box says Arkview wireless-n 802.11N PCI Adapter with speed booster. The item code is PCI-802N.

I have a way to install drivers for it that *might* work, but I would have to get rid of gNewSense (like hardy heron, only with no proprietary software whatsoever) and go with regular Ubuntu for that.

---

### Post by wangsuda on 2009-03-20
If your card truly needs a Ralink driver, then click this link [https://answers.launchpad.net/ubuntu/+question/64171](https://answers.launchpad.net/ubuntu/+question/64171) to install one. Worked great for me.

---

