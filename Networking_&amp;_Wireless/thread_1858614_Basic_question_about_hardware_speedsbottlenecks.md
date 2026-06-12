---
title: "Basic question about hardware speeds/bottlenecks"
date: 2011-10-12
forum: Networking &amp; Wireless
---

### Post by elpedr0 on 2011-10-12
Hi,

I'd appreciate some advice on my latest project to repurpose an old Dell 3000 into a media/file server using linux server edition. The mobo is IDE, but I'm going to use a Sata II drive and was wondering what sort of PCI card to get so that I don't create any avoidable bottle necks.

Drive: WD20EARS Western Digital SATA II 64MB cache 5400rpm
Mobo: Dell 3000 motherboard (not sure what specs are relevant, but [here's a link]("http://support.dell.com/support/edocs/systems/dim3000/en/SM/specs.htm#wp1075776") to dell site)
NIC: integrated network interface capable of 10/100 communication.
Network infrastructure: All machines wired to my router via Ethernet cables

There are plenty of PCI cards on ebay that support SATA I (i.e. 1.5Gbps), which obviously doesn't get the most out of my hard drive. But is that the limiting part of my set up? I.e. if I got a SATA II PCI card, would I achieve faster data transfer in my network, or is my speed capped by another component?

I'd be willing to spend a little bit on other cheap components (e.g. 10/100/1000 NIC?), if they'd be cost effective.

Any advice appreciated.

Cheers.

---

### Post by dave01945 on 2011-10-12
i think your bottleneck will be either in the pci or the network but it all depends on how many devices will be streaming from the media server at any one time, the pci bus can do 133MB/s and with gigabit network adaptor you will get approx 100MB/s so a sata 1.5G/s will be plenty for a pci slot. the pci can run faster than the network is capable of so the network will be what slows it down and also if any other devices connect with wireless they won't even come close to that speed.

also the pci bus is often shared with other components in the computer so you may not get the full speed

---

### Post by collisionystm on 2011-10-12
> **elpedr0 said:**
> Hi,

I'd appreciate some advice on my latest project to repurpose an old Dell 3000 into a media/file server using linux server edition. The mobo is IDE, but I'm going to use a Sata II drive and was wondering what sort of PCI card to get so that I don't create any avoidable bottle necks.

Drive: WD20EARS Western Digital SATA II 64MB cache 5400rpm
Mobo: Dell 3000 motherboard (not sure what specs are relevant, but [here's a link]("http://support.dell.com/support/edocs/systems/dim3000/en/SM/specs.htm#wp1075776") to dell site)
NIC: integrated network interface capable of 10/100 communication.
Network infrastructure: All machines wired to my router via Ethernet cables

There are plenty of PCI cards on ebay that support SATA I (i.e. 1.5Gbps), which obviously doesn't get the most out of my hard drive. But is that the limiting part of my set up? I.e. if I got a SATA II PCI card, would I achieve faster data transfer in my network, or is my speed capped by another component?

I'd be willing to spend a little bit on other cheap components (e.g. 10/100/1000 NIC?), if they'd be cost effective.

Any advice appreciated.

Cheers.

Newegg 
[B][SIZE=1]SYBA SY-PCI40017 PCI SATA II (3.0Gb/s) Controller Card[/SIZE]
[/B]

[http://www.newegg.com/Product/Product.aspx?Item=N82E16816124031](http://www.newegg.com/Product/Product.aspx?Item=N82E16816124031)

Make sure you put on some sort of usb hard drive to sync your stuff to...dont want to lose all those media files!

---

### Post by elpedr0 on 2011-10-18
Many thanks for your help. I ended up buying a PCI Sata I card for GBP 4 on ebay. It's not branded but the vendor said that it would work with Linux (fingers crossed)

Should I just try and plug it in and start the system up? Or is there something that I should do first to maximise my chances of getting it working?

I'm using Ubuntu server 10.04.

---

