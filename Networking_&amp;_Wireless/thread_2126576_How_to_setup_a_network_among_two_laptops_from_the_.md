---
title: "How to setup a network among two laptops from the command line?"
date: 2013-03-17
forum: Networking &amp; Wireless
---

### Post by kramer65 on 2013-03-17
Hello,

For a project which I am doing I need to be able to connect two laptops to each other via wifi. There is no external internet connection, so it's not like I am first connecting them to a router or something which hands out internal ip addresses.

I want a program which I write to be able to access the other laptop using the zeroMQ messaging library. For this I need the other laptop its ip address.

Does anybody know how I can setup a simple network (doesn't need to be secure or anything) in which each laptop has an ip address? Do I even have to set up a network for this? All tips are welcome!

---

### Post by Lars Noodén on 2013-03-17
You should be able to just manually assign an ip address to the interfaces on each machine and then connect directly.  [ifconfig](http://manpages.ubuntu.com/manpages/precise/en/man8/ifconfig.8.html) run with sudo should do that.  I find [ip](http://manpages.ubuntu.com/manpages/precise/en/man8/ip.8.html) to be too complex.

---

