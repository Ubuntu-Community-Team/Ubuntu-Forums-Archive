---
title: "Giving internet to other computers w/o router"
date: 2011-05-05
forum: Networking &amp; Wireless
---

### Post by Townley89 on 2011-05-05
Hey team,

If I have a desktop with a USB wifi adapter connected to the internet through an ethernet cable, is it possible to create a wireless network using the adapter that will allow other users to connect to the internet through mine? I'm in a fairly low-tech place for the next few weeks and getting a router isn't likely. 

If it's possible, anyone have links or instructions for how to do it? 

Thanks!

---

### Post by Jake.Debord on 2011-05-05
I'm a little confused by your post... You are connected to the internet by Ethernet correct? 

But, you also have a USB wireless network adapter that you want to try to broadcast WIFI from??? Could you provide some details about the USB adapter?

---

### Post by Jake.Debord on 2011-05-05
Take a look at this:

[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

May not be what you where hoping for, but unless your laptop supports access point technology then this will probably be the best you can do.

---

### Post by Townley89 on 2011-05-05
Hi all, I'll clarify a bit further.

Essentially, I'd like to turn my computer into a wireless router while still maintaining the ability to use it. I have a wireless card that is not connected to any network and an ethernet connection to a modem. 

I would create an ad-hoc network (as helpfully mentioned in your link above) and allow other computers to connect to it (windows and mac machines as well) and afford them internet access through this network, presumably on the same IP address as my own computer. 

Is there a program that can do this with a reasonable amount of ease? I'm willing to tinker, but I'm not what one might call "technologically gifted"

Many thanks,

---

### Post by Townley89 on 2011-05-05
Oh and about the USB adapter, I have an RT2860 Ralink PCIe wireless N adapter. I also have a generic Belkin USB Wireless G adapter.

---

### Post by spiky001 on 2011-05-05
Yo can set this up by yourself quite easierly.dos e the usb wireless dongle work on the pc, can yo see other wireless networks around

---

### Post by Jake.Debord on 2011-05-06
You may try the network manager to set it up that way, what are the other systems running?

---

### Post by Jake.Debord on 2011-05-06
If the two machines are both Ubuntu you may try this follow site:

[http://unixlab.blogspot.com/2010/01/setting-up-ad-hoc-wireless-network.html](http://unixlab.blogspot.com/2010/01/setting-up-ad-hoc-wireless-network.html)

This should still be helpful if the other systems you are running are windows or mac, just following the guide for Host A. Then, setup a new network connection on the other system entering the same information you provided for your ubuntu. If your other system is windows or mac it should be a breeze to set them up as they have wizards for setting that sort of thing up.

Hope that helps.

---

