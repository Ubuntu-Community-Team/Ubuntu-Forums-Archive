---
title: "Can access internet, but others cant access me."
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by Hailwood on 2010-03-22
Hi guys,

Well i have an ubuntu web server setup (NB not using server edition)
The server works fine... for a while

then all of a sudden it just drops.
I.e i wont be able to access the mail server, the ftp server, the ssh server, the web server, anything on that computer, yet i can still ping it, and the computer can still browse the internet.

the strangest thing is that this will, after a while ie a few hours fix itself, and then it will randomly do it again.

does anyone have any ideas of what could be causing this, eg any programs that could be blocking it, anything at all?

I have tried rebooting the computer, rebooting the router, everything

Regards,
Hailwood

---

### Post by johnson.d on 2010-03-23
You can check whether the ip-address that is configured in the web-server is the same as in the OS. If there were a DHCP server in the network your ip would have changed to a new one when the lease got expired.

In your ip is static, check whether if there is any other system with the same ip-address.

---

