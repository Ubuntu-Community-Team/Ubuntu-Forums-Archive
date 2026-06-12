---
title: "(Help) My internet will not connect on a new desktop install"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by mrparadigm on 2009-04-27
[SIZE=2]          I am new to linux but very familiar with computers and have installed 9.04 i386 on a [/SIZE][SIZE=1][SIZE=2]Dell Dimension 3000 Desktop. Everything has loaded fine accept that it will not connect to the Internet. The desktop would be connected by Ethernet to a Motorola dsl router from ATT (non wirless). The router works because this is was written using that same connection on a laptop also using 9.04. What information do you need from me to help remedy this problem?[/SIZE]

[SIZE=2] 
:smile:Any help would be greatly appreciated as I have just converted my parents to Ubuntu because of all the problems they had with Windows![/SIZE][/SIZE]

---

### Post by Iowan on 2009-04-27
If you're unplugging the laptop from the router and plugging in the desktop, you may need to cycle power to the router.  Some modems "lock onto" the MAC address and won't wouk unless reset.  I'd think a router wouldn't do that, but might be worth a try.
Beyond that, verify (ifconfig -a) that the machine has an IP address.

---

