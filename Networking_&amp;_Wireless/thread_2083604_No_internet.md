---
title: "No internet?"
date: 2012-11-13
forum: Networking &amp; Wireless
---

### Post by JungAk on 2012-11-13
Hello,
I recently installed Ubuntu on my Desktop via the Windows Installer so I could dual boot.  The installation went smoothly.  Though upon booting up Ubuntu, I found that I had no internet connection despite being able to connect fine on my Windows Partition.  How can I fix this?
Cheers,
Jung

---

### Post by darkod on 2012-11-13
First, installing ubuntu inside windows (wubi) using the windows installer is not a dual boot. It's like a virtual ubuntu inside windows, not on its own partition.

If you are talking about the wired connection, it's very rare if it doesn't work by default. Get your adapter version and google around to see if there are any issues with drivers mentioned. Usually you can get the list of the PCI devices including the network adapter with:
lspci

If it's wireless, usually you need to add drivers to work.

---

### Post by Bucky Ball on 2012-11-13
*Thread moved to **Networking & Wireless***

---

### Post by JungAk on 2012-11-13
I'd like to apologise for putting this in the wrong place and not knowing the wubi is more of a "virtual machine" rather than dual boot. I'm new to Linux and Ubuntu.

I googled around in regards to my Network Adapter (nvidia nForce 10/100 mpbs Ethernet) and I couldn't really find much. Perhaps I am searching for the wrong thing, I've never been very good at it.  Either way, I tried to put in my network information manually.  Despite Ubuntu saying that I was now connected, I still couldn't access my internet. Sorry for being so clueless.

---

### Post by Bucky Ball on 2012-11-13
Are you using a static IP address? If so, you are also going to need the DNS ip to get onto the net (else you will connect with the router but can't go any further).

---

### Post by JungAk on 2012-11-13
I'm pretty sure my IP is static.  By DNS ip do you mean DNS server? If they are the same then I already tried putting in that information manually and it didn't work.

---

### Post by Bucky Ball on 2012-11-14
In that case, are you sure your access point, probably your router, is not trying to serve you an IP address in the same range as the static one at the same time? Check the router config and see if it is has the DHCP server enabled.

You can either switch it off or set it to serve in a range outside your static IP. E.g. if your ip is 192.168.0.103 let the DHCP server serve IPs in the range of 192.168.0.110-120, if you get me ...

---

