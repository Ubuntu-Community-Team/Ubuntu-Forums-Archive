---
title: "Accessing a Windows XP Shared Printer from Ubuntu 10.10"
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by irishetalon007 on 2011-03-08
I'm using Ubuntu 10.10 and I'm able to print to a windows XP shared computer and all's fine and dandy.

When I enable gufw printing no longer works. This is no good because everyone in my household has the Mac mentality "AAAARRGGGH why doesn't this just WORK why can't we get a MAC! Mac's are better they JUST WORK!" lol

Anyways I have the printing XP computer with a static IP address 192.168.xxx.xxx so I have that IP address open for all port ranges, but I notice in the gufw log when I go to print it says 
"UDP 34282 smbspool" as a (black-font) request from (or to) address "*" (asterisk), which I take to mean that it doesn't know the address the request came from or something.

I also notice that the UDP address shown is different every time.

In addition to (or along with) the above request for help, I have a few questions about GUFW.

1. What is the difference between the black and red colored lettering in the log?
2. If I want all inbound traffic from my LAN to come through, how do I type this in the advanced section of the rule additions? Currently I have it typed as follows:

FROM: 192.168.xxx.2   port  1:65535
TO:   192.168.xxx.255 port  1:65535

is this correct? or should the FROM port be just 1 and the TO port be just 65535?

Thanks a million!

---

