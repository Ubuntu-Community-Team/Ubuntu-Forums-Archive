---
title: "Alternative to RTL8191SEvB on a Lenovo T410?"
date: 2011-01-18
forum: Networking &amp; Wireless
---

### Post by kmkz89 on 2011-01-18
Hi all,

I just received a new Lenovo T410 with RTL8191SEvB wireless controller. Unfortunately like many people on this board I am having huge WiFi problems when running Xubuntu 10.10. I've tried switching kernels, changing my router settings, switching from network-manager to wicd, and all sorts of other black magic. The only (temporary) solution I've found is to rmmod r1892se_pci/modprobe r1892se_pci every few minutes, which gets old fast.

Anyway, I'm looking for an extremely painless long-term solution where cost is not really an object (I already paid a ton for the laptop, I want it to work perfectly). Clearly this Realtek controller has problems that aren't going away any time soon... someone in another thread was on the phone with their engineers and didn't get anywhere fast. I guess what I'm looking for is an ExpressCard WiFi card that has GREAT Linux support. Anyone know of anything along these lines? I saw someone else pull this off, but he/she didn't mention the model they purchased.

Any help would be great!

Thanks

---

### Post by chili555 on 2011-01-19
This page suggests several Intel cards that work pretty well:  [http://www.thinkwiki.org/wiki/Category:T410](http://www.thinkwiki.org/wiki/Category:T410)>     * Intel Centrino Ultimate-N 6300
    * Intel Centrino Advanced-N 6200
    * Intel Centrino Advanced-N + WiMAX 6250
    * ThinkPad 11b/g/n Wireless LAN Mini-PCI Express Adapter II If you click on the last link, you'll see that the Thinkpad device is your Realtek.

You have to be a bit careful about which card you swap in because of whitelisting: [http://www.thinkwiki.org/wiki/Problem_with_unauthorized_MiniPCI_network_card](http://www.thinkwiki.org/wiki/Problem_with_unauthorized_MiniPCI_network_card)> **Affected Models**

All machines with integrated WiFi, or machines with WiFi added By the way, I love the T410; I'm jealous.

Would you want to take a shot at troubleshooting the Realtek?

---

