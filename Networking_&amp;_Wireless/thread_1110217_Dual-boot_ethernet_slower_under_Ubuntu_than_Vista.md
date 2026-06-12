---
title: "Dual-boot: ethernet slower under Ubuntu than Vista"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by therangemaster on 2009-03-29
I have encountered an issue with my dual-boot workstation. It is a HP Pavilion a6132P with a Realtek RTL8111C ethernet controller. I am running Intrepid 8.10 x86_64 and Vista 32-bit.

When I check my speed with any of the test sites (speedtest.com, toast.net, etc.) I see about 2.5 Mbps download under Ubuntu and 7.5 Mbps download under Vista. Upload for both is about 2.5 Mbps. I tested this numerous times to make sure it wasn't an intermittent error caused by network or server load. It is very consistent.

I downloaded the linux driver for 2.6.x directly from Realtek, compiled it and loaded it into the kernel. I verified that it was loaded and not the original driver. It didn't make a difference.

I don't change the hardware or cabling in any way when I dual-boot. Has any one else seen this discrepancy in network speed between the OS's? Realtek states on their site that the driver is compatible with 64 bit Linux and it compiled cleanly. It is the driver I am using to post this.

I have read other posts saying this Realtek card is a dog. Just wondering if I can fine tune this to fix the speed issue or should I get another card. Recommendations for a new card would be appreciated as well.

---

### Post by TBerk on 2009-03-29
I'll bet it's just the default configuration in Ubuntu, not the card.

Lets look for "How do I configure..." type posts, esp things like the MTU, etc.

Also, I found some very interesting info re: Disabling IPv6 (that is, if you aren't needing it).  IPv4 remains the default across the planet, but it seems IPv6, while the future, well it's deactivation in this case may well speed up your connection.

What do the Search Archives provide?


TBerk

PS- what realtek card are you using? And what is it's chipset? (I'm using one myself; rt2860sta btw.)

---

### Post by therangemaster on 2009-03-29
To anyone else with this problem, I found a solution. I followed the optimization instructions here:

[How to Optimize your Internet Connection using MTU and RWIN]("http://ubuntuforums.org/showthread.php?t=872346")

Once I increased the MTU to maximum, my upload and download speeds on Ubuntu exceeded my speeds on Vista.

I will follow up if I find any other methods to optimize my network connection.

Thanks TBerk for the suggestion...

---

