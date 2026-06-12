---
title: "Integrated Wireless troubles - Gateway notebook"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by JustSomeCanuck on 2009-04-01
Hello,

I recently got a Gateway T1631 notebook computer and installed 64 bit Hardy (8.04) on it. Everything works perfectly except the built-in wireless LAN. It's a Realtek 8187SE.

When I type "sudo lshw -C network" in the terminal, it says "UNCLAIMED" for the wireless. The built in help says that means it just needs a driver, and then it should work.

I wanted to connect it to the wireless network at my university. They give these instructions on their website:

[http://www.utm.utoronto.ca/index.php?id=7008](http://www.utm.utoronto.ca/index.php?id=7008)

At the university, trying with Ethernet also didn't work (there are no instructions for that on the website).

I got the driver from Realtek's website and put it on the notebook with a USB, but I don't know how to get NDISWrapper on it.

Help!

---

### Post by Sam Lars on 2009-04-03
You should be able to fine the Ndiswrapper packages through here:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

