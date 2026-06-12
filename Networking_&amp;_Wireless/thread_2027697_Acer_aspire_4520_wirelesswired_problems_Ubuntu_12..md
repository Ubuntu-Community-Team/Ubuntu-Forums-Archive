---
title: "Acer aspire 4520 wireless/wired problems Ubuntu 12.04"
date: 2012-07-16
forum: Networking &amp; Wireless
---

### Post by Bruce90 on 2012-07-16
Hello,

I am very new to the Ubuntu 12.04 os and Ubuntu in general. I recently installed it on my laptop. Now with an Ethernet cable correctly connected the wired network connects and then immediately disconnects. I wireless option does not even appear in the network tab. Any help would be greatly appreciated.

Thanks,

Shane

Ps: know my wireless network works because my phone is connected and that is how I'm posting this question.

---

### Post by OM55 on 2012-07-16
It is very possible that your Acer (as most Acer laptops do) has a proprietary Ubuntu network driver. Just go to System Settings and click on Additional Drivers. The system will search what's available based on your hardware. If it finds the Broadcom driver and it is marked as "Not in use" - that is what you need. Just switch the selection to "Use" and after a short while the window will close. Restart the system and you should be up and running.

There is only one problem though: In order to install anything you need... Internet connection... which you currently have a problem with.

However, based on the name/model of your laptop you can also use another computer to search and find the proprietary network driver in the Ubuntu repositories (or directly from Acer) and then install it using a USB key or a CD.

---

### Post by pmalbec on 2012-08-27
I have the same Acer Aspire 4520. I did what you said, I went to additional drivers, enabling this broadcom driver (it went to green light, it says it is ok) re-initialize the laptop, and.... nothing.
What can I do?

Thanks in advance,

Paul

---

