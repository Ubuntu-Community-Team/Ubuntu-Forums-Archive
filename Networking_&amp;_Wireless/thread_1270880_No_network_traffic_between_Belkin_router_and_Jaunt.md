---
title: "No network traffic between Belkin router and Jaunty laptop"
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by meatychunks on 2009-09-20
Hi,

I have a Belkin N-Wireless F5D8233-4v3 router to which I currently have successful wireless connections with PCs running XP Pro, Ubuntu Hardy, Mythbuntu Jaunty and Jaunty Netbook remix.

I've recently installed Jaunty on an HP NC6220 laptop. It has an Intel Wireless 2200BG (Calexico2) network controller. This laptop was previous installed with XP Pro and connected wirelessly to the Belkin router with no problems.

Since installing Jaunty on the laptop, I've found that after every suspend or shutdown event, I have to reset the router in order for the laptop to function correctly on the network. There is a strong wireless signal, and the laptop *is* connected and has an IP assigned. However, I cannot ping any other machine or the router on the network.

I had thought it may be a problem with wireless-n, but once the router is reset, wireless functions perfectly from the laptop with or without n enabled on the router - until the next suspend or shutdown event on the laptop.

Can anyone please provide any advice?

Many thanks.

---

### Post by meatychunks on 2009-09-22
Anyone had any experience of a problem like this? Anyone got any pointers?

---

### Post by Cuba71 on 2009-09-22
I'm not familiar with Belkin routers, my only comment is to make sure that the Network Mode in the router is set to "Mixed" meaning, wireless n (the router) can talk to wireless bg (Intel adapter)

---

### Post by meatychunks on 2009-09-23
Thanks Cuba71. I can confirm that the wireless is set to enable n- b- and g-mode. In fact, I disabled n altogether though this had no effect...

---

### Post by meatychunks on 2009-09-24
Seems I have it working for now.

Downloaded latest firmware from [http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/) and dropped it in my /lib/firmware directory. After a reboot all seems good.

---

### Post by meatychunks on 2009-09-24
Looks like I spoke too soon...

A few reboots and suspends later and I'm back where I started.

Anyone any experience of getting this intel 2200 card to work properly?

---

