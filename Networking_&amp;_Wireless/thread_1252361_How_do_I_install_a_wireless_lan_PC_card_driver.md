---
title: "How do I install a wireless lan PC card driver"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by Ralphieman on 2009-08-28
I'm trying to get Ubuntu working on an old IBM Thinkpad T30. Everything is working great, but I can't get the 3Com Wi-Fi plugin PC card to work (it worked fine in Windows and MEPIS). I can see it when I run sudo lshw -C network (it shows up as product: 88w8335 [Libertas], vendor: Marvell Technology Group), but it has no logical ID and the network says UNCLAIMED. I believe that I need to install a driver, but I don't know how to do that and I can't find the instructions to do so on this forum. I have the Windows driver disk for the card, but those don't do me a lot of good. 
 
Can someone provide some guidance on finding/installing drivers for this? I have a wired Ethernet port so I can plug into my router to download anything. 
 
I'm brand-new to Ubuntu, so please give any directions in dummy terms. I can get to a terminal window and find anything on the menu system ... but that's about it.
 
Many thanks ...

---

### Post by bowhuntr09 on 2009-08-28
no expert, but ndisgtk helped me, it allows you to install the drivers from your windows drivers.

---

### Post by Ralphieman on 2009-09-02
Success!  Thanks!!

---

