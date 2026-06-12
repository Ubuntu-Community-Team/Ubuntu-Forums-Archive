---
title: "Ad-hoc ethernet network - possible?"
date: 2012-11-10
forum: Networking &amp; Wireless
---

### Post by Wayfar3r on 2012-11-10
I have a bit of an interesting issue. I purchased a piece of used network enabled equipment online. The device connects through an Ethernet port on the back and is configured for an ip address at setup. Issue is, it currently has the ip address 150.216.204.226, I'm unsure of the current subnet. I need to telnet in so I can change the ip address to something on my subnet. Finding an appropriate subnet is the first order of business. I'll be honest, I am not entirely sure how subnets work in terms of the bits passed across the network and reading the article on wikipedia has left me with just as many questions. If I was to choose the highest subnet, 127.255.255.255, would that guarantee that I could communicate with the device? Or would it be an issue if the previous owner set up some other subnet (127.255.255.253, etc.)? Once I have the subnet, I believe that I can just set up a static connection in /etc/networking/interfaces and connect the device directly to my laptops ethernet card- although I will need to use the prefix instead of the mask and I'm not sure how to do this or what I should enter as the gateway. Can some on give me a push in the right direction? Thanks!

---

### Post by ahallubuntu on 2012-11-10
You probably can't simply connect to it with an ethernet cable.  If you have what's called a "crossover cable" you could do that.  Some modern network cards supposedly detect this configuration automatically and will let you do this sort of network with a regular ethernet cable, but I've never managed to get that to work.

If you have a switch or a router, you can do it that way without any special cable.

If you have a switch, connect your computer and the device to the switch with ethernet cables.  Set a static IP on your computer to, say, 150.216.204.225 with a subnet mask of 255.255.255.0 (should be fine).  Make sure your computer is otherwise not on the internet.  (And if you are using a desktop edition of Ubuntu with Network Manager, use that to set the static IP, not the interfaces file.)

If you have a router, configure it with a LAN IP address of 150.216.204.1 subnet mask of 255.255.255.0 .  Make sure DHCP range ends below 150.216.204.226 so you won't get the same IP as the device.  Then you won't have to set a static IP on your computer - the router will assign one in the subnet.  (Again, make sure the router isn't connected to the internet.)

Once you are connected up, see if you can ping the device.

Sure there's no way to reset the device to factory settings with a little button or something?

---

### Post by Wayfar3r on 2012-11-10
Thanks ahallubuntu! I hooked up an old router and that did the trick - easy enough! I thought modern nics would work without a crossover cable as well but no such luck. Telnet connected but it looks like the previous user set up a username and password and I don't know either. Will have to either look for a reset switch, as you suggested, email the previous owner, or just use it on a second network - a perfectly viable option. Thanks again!

---

