---
title: "Ubuntu Breezy and rt24xx"
date: 2006-01-16
forum: Networking &amp; Wireless
---

### Post by moises73 on 2006-01-16
Hi all,
I have a Toshiba laptop which I had set up with Hoary Hedgehog and WinXP dual boot.  I had Wi-Fi using a RaLink RT24xx mini-PCI card.  I used the source code provided by the company and it installed perfectly :grin: .  I recently upgraded from Hoary to Breezy Badger, I attempted to use the code mentioned above to install the same, but it does not install :-( .  The make file calls gcc3.4, but Breezy uses gcc4.0.  I installed the gcc3.3 that is in the installation cd from Breezy, but this did not work.  Does anyone know how I could make this work?  

Thanx

---

### Post by Lambert on 2006-01-16
Breezy uses 4.0 for all apps but kernel is compiled with 3.4. Because this is a kernel module it will also need to be compiled with 3.4

Can you post the output you get when trying to make so we can see the errors?

I also believe rt2400 driver comes with breezy so I don't think it needs to be compiled. Post the output of this command

sudo lshw -C network

---

### Post by moises73 on 2006-01-16
*-network:1 DISABLED
        description: Wireless interface
        product: Wireless PCI Adpator RT2400 / RT2460
        vendor: RaLink
        physical id: a
        bus info: pci@02:0a.0
        logical name: ra0
        version: 00
        serial: 00:08:a1:5b:12:79
        width: 32 bits
        clock: 33MHz
        capabilities: bus_master cap_list ethernet physical wireless
        configuration: broadcast=yes driver=rt2400 multicast=yes wireless=RT2400P CI
        resources: iomemory: 20002000-20003fff irq:11

I did enable the card before I attempted to use it, with no luck to connect.  I also tried to connect using windows, no luck either.  I did this at a public network.  I would assume that the network was down that day, may be that is why I though I had to get the driver for the card.

---

### Post by Lambert on 2006-01-16
>          configuration: broadcast=yes driver=rt2400

This line tells me driver is loaded and bound to the device so you should just have to configure the connection.

---

