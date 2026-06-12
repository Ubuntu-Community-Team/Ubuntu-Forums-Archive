---
title: "DHCP works on wireless, not on wired (intrepid)"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by CoffeeOnMars on 2009-02-15
Hi everyone.
I have discovered that my laptop (Intrepid) can't connect using a wired connection: in the syslog, everything seems normal until the dhcpclient is summoned, and it does not receive a lease; on the other side, connecting to any wireless network works just fine.

On the same wired connection, I have another computer (always Ubuntu Intrepid) and a router, both of them working well. I also tried the laptop on different wired connections, but it never worked.

I also discovered that when using a live cd (Intrepid) dhcp works fine on wired, so I'm assuming it's a configuration problem or a bug in a last version.
Does some one else have this problem, and what do you suggest me to look at?

---

### Post by superprash2003 on 2009-02-15
do you have a sufficient DHCP range set on your router?

---

### Post by CoffeeOnMars on 2009-02-15
My router is the provider's one, I can't see its configuration bit it should be able to handle all the connections, I used it with more elements than now.
I tried again with a clean install, and it actually seems to be a problem with the latest version of dhclient: before updating it works flawlessly.

---

### Post by javabean420 on 2009-02-15
not to downplay the dhcp problem but why not use "static" ip addresses
ever since i started using ubuntu "6.06" i have always setup my ip as static "192.168.1.???" i know that may silly but i find it good to forward ports/TOS from the router

---

### Post by CoffeeOnMars on 2009-02-15
On my home connection I can't use static ips because of provider's limitations, and the laptop I'm having problems with is meant to be used on unknown networks, making DHCP a necessity.

---

