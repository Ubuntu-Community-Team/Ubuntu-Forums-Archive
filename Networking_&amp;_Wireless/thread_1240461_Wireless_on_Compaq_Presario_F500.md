---
title: "Wireless on Compaq Presario F500"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by Genius314 on 2009-08-14
Hi.
I'm having problems connecting to the internet with a Compaq Presario F500 laptop. The wireless card seems to be able to see wireless networks, but can't connect to them.
I can connect to the internet using a USB wireless adapter, so I know it's not a problem with settings or anything. I don't want to have to use one of those, though, since I only have a few and would have to buy another one.

I've found a couple similar questions on the web, but they're either outdated or unsolved.

lspci gives me this information about the card:
> Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)

Thanks.

---

### Post by Metaljaz on 2009-08-14
Trying opening the Synaptic Package Manager and do a search for fwcutter. It should say b43-fwcutter. Mark for install and then apply.

If its not there try this from the terminal window:
(Make sure you are using a wired internet connection)

sudo apt-get update
sudo apt-get install b43-fwcutter

Then Go under System > Administration > Hardware Drivers and make sure the driver is activated. If it is activated in the top right hand corner look for the icon for wireless internet connection. Click on the connection to use it.
Make sure you unplug your wired connection.

---

### Post by Genius314 on 2009-08-15
Well, that helped.
Actually, in order to get the wireless working, I had to *disable* the drivers after installing fwcutter.

Everything works fine now.
Thanks! :)

---

