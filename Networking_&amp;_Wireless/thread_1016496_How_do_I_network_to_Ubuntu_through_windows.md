---
title: "How do I network to Ubuntu through windows?"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by gnarkilljboy on 2008-12-20
I am trying to share files between my windows xp home on my desktop to my Ubuntu on my laptop.

How do I access Ubuntu through Windows XP?

Thanks

---

### Post by jonobr on 2008-12-20
you have a bit of reading ahead of you :p

you will need to install and configure samba,

there are a lot of resources and guides to walk you through,
heres the first one I googled 
[http://www.europe.eclipse.co.uk/Ubuntu/804%20on%20Win%20Network.htm](http://www.europe.eclipse.co.uk/Ubuntu/804%20on%20Win%20Network.htm)
its for 8.04 but there is a lot of info out there

---

### Post by gnarkilljboy on 2008-12-20
Thanks!!!

---

### Post by lykwydchykyn on 2008-12-20
The other option, which is more secure and easier to set up by far, is to install openssh-server on the ubuntu machine, and winscp on the windows machine.  Then you can browse or upload files to Ubuntu from windows by logging in over winscp.

If you want to make your Ubuntu machine act like a Windows server (so that you can browse to it in Windows explorer, or access it at a UNC path like \\myserver\someshare), then as jono says you'll need to install and configure samba.

---

