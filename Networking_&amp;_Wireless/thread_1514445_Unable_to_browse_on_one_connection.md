---
title: "Unable to browse on one connection"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by Kirbysuperstar on 2010-06-21
We have two internet connections here, one through Allegro which goes through an ISA 2004 box and an ADSL2+ connection.

Everything works fine when connected via the ISA box. Windows machines (and last I checked, a Macbook) work fine on the ADSL2 setup, but nothing Ubuntuesque will work properly through it.

DHCP is fine (and the same thing happens with a static IP), it gives a proper address, DNS works fine, it's just whenever a page attempts to load, Firefox will sit at the "Waiting for <site>..." status until it gives up. apt does the same thing.

What I've tested it on so far is:

- a homemade 9.10 box
- an IBM xSeries 346 running 10.04
- an Acer Veriton M460 running 10.04
- an Acer Travelmate 6293 running 10.04

None of them will work with it. The Travelmate and the IBM are dual-boot, both will work fine on the connection under Windows. The Veriton is Windows only (tested using a Live CD) and is much the same.

The router is a Thompson TG782T (Telsta branded). I'm at a loss with this. Any ideas? I can provide more info if needed.

Edit: Just tested Puppy on the Veriton and it was able to browse just fine.

---

### Post by Iowan on 2010-06-21
Mostly to give your thread a "bump", but [this]("http://ubuntuforums.org/showthread.php?t=1376506") thread goes through (or links to information about) checking MTU.

---

### Post by Kirbysuperstar on 2010-06-21
That certainly seems like a viable culprit. I've tried the "ping <router> -c 1 -s <number> -M do" thing with a few different values, but I haven't found one that didn't return a frag needed error yet.

..Is there a quick way to write a batch for a range of numbers and have it output to a file?

---

