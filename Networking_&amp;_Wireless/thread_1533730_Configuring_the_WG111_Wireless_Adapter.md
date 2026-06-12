---
title: "Configuring the WG111 Wireless Adapter"
date: 2010-07-18
forum: Networking &amp; Wireless
---

### Post by Faithless455 on 2010-07-18
Hey guys.  I recently installed Ubuntu 10.04 64-bit alongside Windows XP on my 5 year old gateway desktop.  It's not much of a computer but it runs fine.  Previously, I had been using a Netgear WG111 Wireless with Windows XP and it worked great.  I've spent the past few hours reading threads on how to connect this adapter to my wireless network and nothing I've seen seems to work.

Tell me what information you want me to give you guys and I will.

Thanks,
EjG

---

### Post by Faithless455 on 2010-07-19
I believe bumps are allowed?

 [Bump]

---

### Post by Faithless455 on 2010-07-24
An update:

I've installed ndiswrapper-common, ndiswrapper-utils-1.9, and ndisgtk.  Using ndisgtk, I've added the wg111 driver, which recognizes that the corresponding hardware is present, as expected.  However, it still won't allow me to connect to the internet.

I feel so close, what am I missing?

Thanks,
EjG

---

### Post by Faithless455 on 2010-07-25
[Bump]

EjG

---

### Post by Faithless455 on 2010-07-26
Fifth time's the charm...?

Another brief update.  I believe the issue is a matter of system architecture, my Ubuntu sector is 64bit and my XP sector is 32bit.  I believe I've located a driver download site ([found here]("http://drivers.softpedia.com/get/NETWORK-CARD/NETGEAR/Netgear-WG111v2-Driver-201.shtml")), but how can I tell if it is 64bit or 32bit?  Or are both in the same file?  Or am I simply clueless when it comes to system architecture?

Thanks,
EjG

---

