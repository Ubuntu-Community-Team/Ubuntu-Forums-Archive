---
title: "mifi and wifi"
date: 2011-07-15
forum: Networking &amp; Wireless
---

### Post by dpwilson on 2011-07-15
Hopefully someone can help me out here.  My internet service is a cellular wireless.  I use a Mifi wireless broadband.  I also have a wireless router hooked up to my computer from my previous ISP.  My question is can I use both of these connections at the same time.  I would like to use the wireless router to  connect to other devices; printers, share files, etc.  I cannot figure out how to have both as active though.  If I select the mifi, then I have no connection to the wireless router and vice versa.

Is there a way to use both at the same time?  Any help is greatly appreciated.

I am using ubuntu 11.04 currently

Thanks.

---

### Post by jmoorse on 2011-07-16
Mifi provides a wireless network to join right?

If so, you are asking if you can join 2 wifi networks (mifi, wireless router) at the same time.  The answer is: AFAIK not without multiple wireless cards.

---

### Post by dpwilson on 2011-07-17
Thats what I was afraid of.  Thanks.

---

### Post by dpwilson on 2011-07-25
I had the answer to my question all along.  I have a couple of dongles laying around and used them, now I have internet on one and home networking on the other.

---

### Post by paulpsicle on 2011-07-29
You can plug the MiFi in to a usb port. Then run "sudo eject /dev/sr1" and then you can connect to it as a Mobile Broadband connection in NetworkManager.

---

