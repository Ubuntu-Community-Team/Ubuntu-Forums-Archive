---
title: "Loss of internet connection triggered by downloads/activity"
date: 2013-01-20
forum: Networking &amp; Wireless
---

### Post by sunnybubblegum on 2013-01-20
I have a bit of an unusual problem (as far as I've seen) regarding my freshly-installed [vanilla] Ubuntu 12.04 desktop's internet connection.  I use a Linksys WUSB54GC wireless USB dongle.

I have an internet connection whenever I boot up my system. However, it's usually after I start downloading something or doing something network-intensive -- games, for example -- that the connection stops working. It can sometimes work for a long time (half an hour, 45 minutes) before it stops working, or it can be a matter of minutes.

Even after the connection is gone, my wireless adapter and my router are still talking, and show both a strong signal and a high speed. But there is no connection being made to the ISP. The only thing I can do at that point to get my connection back is to reboot the entire CPU (and even then, I usually have to hold down the power button because something is perpetually frozen). I haven't seen any others report quite this sort of thing among my searches.

What could be the cause of this? Is there anything I can do to fix it?

---

### Post by sunnybubblegum on 2013-01-20
My apologies.

I now believe I see what the problem was, and I'm pretty sure it wasn't Ubuntu. It was a faulty extension USB cable connecting my wifi adapter to my CPU. When I finally suspected it (I had gotten the cable via a less reliable outlet), I plugged the wifi adapter in directly, and there have been (so far) no more problems.

Again, my sincere apologies for jumping to conclusions. It was just very frustrating without any indication. A good lesson in having at least some quality of hardware.

---

### Post by ZippyUbu on 2013-01-20
Hi, I also experienced this with an extension cable on a USB adapter. After changing to directly connecting the adapter the issue went away. I don't know if the extension was faulty but I do remember reading somewhere that some manufacturers advise not to use extensions... 

Glad you got sorted ;-)

--
Zu

---

### Post by sunnybubblegum on 2013-01-20
> **ZippyUbu said:**
> ..but I do remember reading somewhere that some manufacturers advise not to use extensions...

Just curious, do you remember if this advice applied to using USB extension cables in general? I'm still using one on my keyboard, but I wonder if it will cause me intermittent system problems down the road.

Thanks for your reply.

---

### Post by ZippyUbu on 2013-01-20
The article I was referring to was only on USB Wifi Adapters... If I come across it again ill post for you... I'd leave the extension in place for your keyboard and if you start to have trouble, remove it and see how you get on... ;-)

--
Zu

---

### Post by sunnybubblegum on 2013-01-20
I appreciate it. Seems like a sound way to go.

---

### Post by tgalati4 on 2013-01-21
The wireless chips in those USB dongles get driven pretty hard, so they do tend to fail.  When the chips fail, they don't have the power to push through a 6' cable, but may work without a cable.  However, they will die altogether with or without a cable.  Try a different brand of USB dongle and read the reviews.

---

