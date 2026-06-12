---
title: "Yes, another Broadcom 4306 issue"
date: 2012-05-13
forum: Networking &amp; Wireless
---

### Post by pmonacular on 2012-05-13
Hello!  I generally pride myself on fixing things myself, but 2 days of searching hasn't yielded a positive result for me yet.  I'm using Lubuntu 12.04, and I'm getting what seems to be the very common message of "firmware missing" when I check the wireless network connections.  After searching for and reading dozens of pages, I've gotten as far as downloading and installing B43-fwcutter, but if there's another step after that, I'm not sure what it is.  If anyone can help, I would be extremely grateful.  And so would my ethernet cable.  It's lazy, and doesn't generally like to be active.

The card is a Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

I can include more info if needed (I have seen the how to post a wireless issue page), but I'm hoping that I've got most of it down and am just missing 1 or 2 more small steps.

---

### Post by chili555 on 2012-05-13
Please let me see:```
lspci -nn | grep 0280
```Thanks.

---

### Post by pmonacular on 2012-05-13
Thanks for having a peek!

01:04.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

---

### Post by chili555 on 2012-05-13
Please open a terminal and do:```
sudo apt-get install linux-firmware-nonfree
```Reboot and let us have your report.

---

### Post by pmonacular on 2012-05-13
Worked like a charm!  Thanks so much!

---

### Post by chili555 on 2012-05-13
Awesome! Would you please use thread tools at the top to Mark Solved? The searchers will appreciate it.

---

### Post by pmonacular on 2012-05-13
No problem.  Thanks again.

---

### Post by jim3108 on 2012-09-29
Thank you all for your posts on this thread - this worked a treat for me.

For your information, I am running:

Acer Ferrari 3200 Laptop with Broadcom B4306 v3 Wireless

... This thread made Ubuntu LTS 12.04.1 recognise the wireless adapter and it works perfectly!

Thanks again guys!!

J.

---

