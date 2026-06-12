---
title: "Can't connect to WEP wireless"
date: 2011-05-31
forum: Networking &amp; Wireless
---

### Post by MES5464 on 2011-05-31
I am using a Lenovo x61 tablet with Ubuntu 11.04 64 bit. I CAN connect just fine with a wireless network except if it has WEP enabled. I think it might be the drivers but I don't want to change anything that will prevent me from connecting entirely. Can anyone suggest a fix for me?

---

### Post by ssreddy555 on 2011-06-01
I would like to mention my own experience here although this is not a solution to your problem hoping that someone else may be benefitted.

I was using WPA2 personal protocol for wireless security & TKIP encryption when I was using Windows. 

When I changed to Ubuntu, at first, wireless didn't work until I installed the driver for my Broadcom WL adopter (This driver does not come installed out of the box). After installing the driver, the notification that 'wireless connection is established" appeared but there was in fact, no connection to the internet. It only meant that the computer & the WL router have established connection; the computer was displaying the SSID of the router. I had a very tough time to get connected to internet until I realized that Ubuntu doesn't work with TKIP encryption & changed it to AES encryption. After that, no problems.

By the way, Windows works with both TKIP & AES.

---

