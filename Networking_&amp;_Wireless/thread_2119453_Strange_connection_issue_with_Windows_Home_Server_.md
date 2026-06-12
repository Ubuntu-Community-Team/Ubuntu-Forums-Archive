---
title: "Strange connection issue with Windows Home Server 2011."
date: 2013-02-23
forum: Networking &amp; Wireless
---

### Post by MrDrizz on 2013-02-23
Hi,
This seems, to me, a bit strange.

When I try to connect to my server, which is running Windows Home Server 2011, from my PC running 12.04 LTS, . I get 

[INDENT]Unable to mount location: Failed to retrieve share list from server.[/INDENT]

However, if I turn my Laptop on, which is running win7 and has the WHS2011 dashboard utility installed. Ubuntu is all of a sudden able to see and connect to the share folders on the server. I can then mount them. Now if I then turn off my laptop, the mounted folder will remain and I can use them but I cannot mount more folders.

so at present if I turn off my PC or reboot I have to also start the laptop so I can get my shared folders mounted again.

It's driving me crazy.

Thanks.
Mark.

---

### Post by MrDrizz on 2013-02-23
I cannot believe this, 5 minutes after posting the message I find the solution.

Here is the tutorial:

[http://www.ubuntututorials.com/connect-windows-7-shares-ubuntu-12-04/](http://www.ubuntututorials.com/connect-windows-7-shares-ubuntu-12-04/)

I just used the server IP rather then MM. 

Thanks for your time

---

