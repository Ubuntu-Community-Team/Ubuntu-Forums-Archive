---
title: "wireless networks not detected"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by bearrider on 2009-04-08
The first time I ever booted up my laptop after installation, the NetworkManager applet worked perfectly and detected wireless networks around me.

Alas. Never again.

Checking around I see that :

lspci tells me I have a : 
[INDENT]02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)[/INDENT]

Restricted devices manager tells me the following are active :

[INDENT]Support for 5xxx series of Atheros 802.11 wireless LAN cards
Support for Atheros 802.11 wireless LAN cards
[/INDENT]
However the NetworkManager applet  doesn't detect any wireless networks in the vicinity, though there are many.

running iwconfig gives :

        [INDENT]lo        no wireless extensions.
        eth0      no wireless extensions.
        pan0      no wireless extensions.
[/INDENT]
running iwlist scan gives :

        [INDENT]lo        Interface doesn't support scanning.
        eth0      Interface doesn't support scanning.
        pan0      Interface doesn't support scanning.[/INDENT]
        
running wifi-radar gives :

        [INDENT]No wifi-device found. Exiting.[/INDENT]
        
and finally, when I look at the grub I see that I'm booting with acpi=off noapic nolapic - does that have anything to do with it? Then why did it work the first time around?

        [INDENT]title		Ubuntu 8.10, kernel 2.6.27-9-generic
        uuid		f7d0c9cf-fd97-4ca8-85a5-91bc37456399
        kernel		/vmlinuz-2.6.27-9-generic root=UUID=2b8e230a-0eda-40f6-9a35-8715426992f6 ro acpi=off noapic nolapic quiet splash 
        initrd		/initrd.img-2.6.27-9-generic
        quiet[/INDENT]

        
How can I have NetworkManager applet or any other tool check and detect for wireless networks?
        
I am at my wits end. I'm trying to convince my mother to convert to linux but am stuck at this step, so pretty please help :)

---

