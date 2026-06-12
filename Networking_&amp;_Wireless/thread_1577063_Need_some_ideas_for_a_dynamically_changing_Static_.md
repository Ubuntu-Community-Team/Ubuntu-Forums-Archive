---
title: "Need some ideas for a dynamically changing Static IP address"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by ToshiBoy on 2010-09-18
I use my laptop on the road all the time to connect to office machines and servers, and one of my pet peeves is that many of the systems I connect to do not a DHCP server, which means that I am forever changing my static IP address to a static address and once I am finished on site, change it back to dynamic.(Add to that, that I can't seem to restart my network unless I reboot... but that's a side issue. When I manually restart, I get a "Ignore unknown..." for both the wlan and eth0 connection.)

Ok, so here is the idea: I want to be able to connect to a network device with a static IP address. At that point, my laptop (currently running the 64-bit flavour of Ubuntu desktop) is still set up with the IP address for  (auto) eth0 being dynamic. I would like to run a script that:

1. Discovers the IP address of the one connected device
2. Changes the IP address of eth0 to a fixed address on the same subnet as the device
3. (optional) opens a web-browser to that IP address

I can write a script that will change the interfaces file to a static address - no big deal. But how do I find the IP address of the connected device without being on the same network? Is there a program that will do that?

I guess if there isn't a way,  I could loop over all IP address ranges until I find one that responds to a ping or something like that? But that would potentially take a long time... it'd be nice if there was a way to probe the connection and find if there is a device trying to communicate and somehow find it's IP address..?

Any ideas?

---

