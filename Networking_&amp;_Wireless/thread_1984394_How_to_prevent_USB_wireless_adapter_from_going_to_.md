---
title: "How to prevent USB wireless adapter from going to sleep?"
date: 2012-05-21
forum: Networking &amp; Wireless
---

### Post by kevdog on 2012-05-21
Wow -- its the first time Ive ever used a USB wireless dongle for a wifi connection (usually use either a wired or pcmcia slot).  Anyway, when the computer goes to sleep (screen turns off) after a few minutes of activity, the wireless connection seems to go down as well.

I've looked in the /etc/acpi however I'm not seeing what I'm looking for.

I do I keep the wireless kernel module loaded and not fall asleep with computer inactivity?

---

### Post by chili555 on 2012-05-21
This sometimes, not always, works:```
sudo vim /etc/pm/config.d/config
```Add one line:```
SUSPEND_MODULES="your_wireless_driver"
```Proofread, save and close vim.

---

### Post by kevdog on 2012-05-21
chili555

Thanks for the advice -- at least I'm looking in the right place and in the right directories.

Just wanted to clarify that what you included in the config file with the SUSPEND_MODULES statement -- actually means the wireless device WILL NOT be suspended.

---

### Post by roelforg on 2012-05-21
> **kevdog said:**
> chili555

Thanks for the advice -- at least I'm looking in the right place and in the right directories.

Just wanted to clarify that what you included in the config file with the SUSPEND_MODULES statement -- actually means the wireless device WILL NOT be suspended.

iirc, it means that when the pc suspends, it'll do the same for the wifi so it won't shutdown.

And you still have pcmcia? I thought those were getting extinct (you may call me a hypocrit because my laptop still has both pcmcia and express card).

---

### Post by chili555 on 2012-05-21
I think it means the module will *not* be unloaded at suspend.

---

### Post by kevdog on 2012-05-21
Well something did the trick --

I did as you suggested above and in addition created a empty wireless executable file owned by root in /etc/pm/power.d/ and then rebooted.  

Thanks guys for tips!!!

And if anyone is looking for a USB wireless chipset that works out of the box -- rt2800usb.  It was sold as an Asus USB-N13 Adapter Wireless-N.  Although it didn't say anything about the chipset on the box, it did state Linux support.

---

### Post by kevdog on 2012-05-22
Correction. I guess it works but sometimes the latency of this connection after a period of inactivity is terrible

---

### Post by roelforg on 2012-05-22
> **kevdog said:**
> Correction. I guess it works but sometimes the latency of this connection after a period of inactivity is terrible

In my exp. sitecom works well.

---

