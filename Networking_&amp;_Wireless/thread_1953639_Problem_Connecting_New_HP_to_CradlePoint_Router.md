---
title: "Problem Connecting New HP to CradlePoint Router"
date: 2012-04-06
forum: Networking &amp; Wireless
---

### Post by cssutto on 2012-04-06
I have a new HP Pavillion.

I have an old ThinkPad connected to it, wireless, and it was a snap to do it.

However, I am having problems getting the HP to talk to it wireless because I can not find how to get it to identify itself to the router.

In other words, do I push a button, give the router a PIN number or what?

I use wicd and I have all of the info filled out in it, but they no speak.

Ubuntu 10.4,  Cradlepoint wireless router using a cell connection to the outside world.

---

### Post by gordintoronto on 2012-04-06
New hardware, old OS, often doesn't completely work. Wireless and sound are usually where problems appear.

Does the Thinkpad also run Ubuntu? Which HP Pavillion?

Does WICD show you the router's SSID? I think most people use Network Manager, so it might be easier to get help if you used it.

---

### Post by cssutto on 2012-04-07
I have discovered a few things since the original post.

claude@claude-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

Wlan0 is not listed.

---

### Post by gordintoronto on 2012-04-07
Try Ubuntu 12.04, see if the wireless shows up in the command:
lspci

---

### Post by cssutto on 2012-04-09
> **gordintoronto said:**
> Try Ubuntu 12.04, see if the wireless shows up in the command:
lspci

I am going to stick with 10.4

---

