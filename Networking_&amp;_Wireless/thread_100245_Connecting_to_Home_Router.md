---
title: "Connecting to Home Router"
date: 2005-12-07
forum: Networking &amp; Wireless
---

### Post by Vermiculus on 2005-12-07
Hi,

New to Linux, I've recently installed Ubuntu, and am very happy with it - but to install it on a friend's computer, we need to know how to connect to his router, which seems to be unsupported.

The model of the **2Wire **package is: **BT Home Network 1200**. Unfortunately, this is the only info it has on it! 

Can anyone give me any advice, or point to tutorials or a driver of some sort? I remember hearing that it's possible to use windows drivers in Linux. That sounds like a last resort kind of thing, though.

Thanks for any help.

---

### Post by mips on 2005-12-07
It will work just fine if you use the ethernet port and ensure that the router does the PPPoE & authentication. Just configure Ubuntu for DHCP or a static IP config.

You dont mention whetehr you are using USB, Ethernet or Wireless as that router supports them all.

---

### Post by Vermiculus on 2005-12-07
Thanks for your help, mips.

In answer to your question: he's using a USB connection. How would he go about configuring it? A list of commands, or link to one, would be nice, as we're both utterly inexperienced with Linux ;).

---

### Post by mips on 2005-12-09
The configuration would be done via a web browser. I dont have any knowledge on that specific router but I'm sure there are lots of guides/manuals on the net.

The easiest option would probably be to contact BT tech support and ask then for configuration assistance. You might not even have to configure anything.

ON the PC all you want to do is configure it for DHCP or a static address.

---

