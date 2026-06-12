---
title: "DHCP table dropped"
date: 2011-05-23
forum: Networking &amp; Wireless
---

### Post by Lysander10 on 2011-05-23
I have a strange problem - when I change the hostname on my Ubuntu server, the DHCP clients table in my router is dropped.

I'm running 32-bit Ubuntu Server 10.10. My router is a Linksys WRT54GL with firmware version 4.30.15. I'm changing the hostname by modifying /etc/hosts and /etc/hostname. I've also tried changing the hostname using the Linux hostname command in a terminal, but this does not seem to behave correctly according to the manpages (it does not actually change the hostname, or update either of the aforementioned files). 

I've also tried using a different router - a Linksys BEFSR41 - but the DHCP table is still dropped when I change the hostname on my server (although this router is not all that different from my other one). 

Does anybody have any idea what could be causing this, and how it might be fixed?

---

### Post by Iowan on 2011-05-23
Perhaps a bit off-topic, but how often (and why) do you change your server hostname? The server gets a DHCP address (or is it a static lease)?

---

### Post by Lysander10 on 2011-05-23
Thank you for your response. I work for a small startup that develops a print server solution for Zebra and OKI thermal printers that is similar to an HP JetDirect, with the addition that it translates various laser and dot matrix printer languages into ZPL and SBPL. We're currently using Fedora as the operating system on our device, but we're investigating switching to Ubuntu (for various reasons, but due partly to longer support and more conservative releases).

Most of our customers are hospitals, and they may assign dynamic or fixed IP addresses to the device we sell them. It is they who need to change the hostname. It's usually changed only once per device, but even so, we can't consider putting such a device into production without knowing what is causing this problem (which has not been a problem with Fedora).

I'm hardly an expert on networks; I specialize in language translators. Ideally my company would have one, but like I said, they're a startup, and can't afford that at the moment, so any assistance would be appreciated.

---

### Post by Lysander10 on 2011-05-23
Also: the DHCP table is dropped, without fail, every time the hostname is changed. We do not change it often (only as needed for testing purposes), and we are assigning IP addresses via DHCP.

---

