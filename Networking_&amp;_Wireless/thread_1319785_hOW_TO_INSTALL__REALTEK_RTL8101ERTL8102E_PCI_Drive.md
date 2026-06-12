---
title: "hOW TO INSTALL  REALTEK RTL8101E/RTL8102E PCI Drivers 9.04"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by El Viejo Lobo on 2009-11-08
I need the drivers and the How To Install for the same,

[I]02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)[/I]
 
The only way I can use my Wi Fi is by using the command line "sudo ifconfig eth0 down"
I try to do something with Realtek WHebsite - This is what I got:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

I do not know how to make it work. Help is needed.

---

### Post by angellika on 2009-11-15
> **El Viejo Lobo said:**
> I need the drivers and the How To Install for the same,

[I]02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)[/I]
 
The only way I can use my Wi Fi is by using the command line "sudo ifconfig eth0 down"
I try to do something with Realtek WHebsite - This is what I got:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

I do not know how to make it work. Help is needed.

I have the same problem. My wifi is not working. Using Karmic on Toshiba Satellite L 515 with RTL8101E/RTL8102E card. 

Hope somebody will help :)

---

### Post by UltraFlynn on 2009-11-16
I'm having the exact same issue with an MSI Wind using the RTL8101E driver. I simply cannot get any driver to work now that I've upgraded to Karmic.

---

### Post by eugenix on 2009-11-16
Having similar problems,

Have yet to test wireless with Karmic, however,noticed problem with LAN after an 8.10 kernel update.  I have a MSi Wind U120.  

ifconfig would show I am connected, but I would be unable to ping or resolve anything.  Oddly, if I clicked on the Network manager icon on the panel, it would show "device not managed."  Every time after reboot, I will have to right click it, then edit connections, add it and put in my MAC address.  Then if I run an ifdown eth0 & ifup eth0.  All of sudden it will work again.

Any advice appreciated.

---

### Post by Dude-PWB- on 2009-11-16
I just went through this with my rtl8192e chipset in my toshiba L500 laptop.

What i did was went to realtek's website and sent an e-mail to their tech support kindly asking them if they had any linux native drivers for my wireless. To my surprise, a few hours later they e-mailed me back with a driver attached.

It was an older driver and wouldn't compile in karmic with the newer kernel, so I e-mailed them again with a list of my compile errors and the next day they e-mailed me again with a newer driver, and it's working like a charm right now.

Send their tech support an e-mail with your install version, kernel version, and tell them you have the 8187se wireless chipset and see if they get back to you. I was pleasantly surprised, I figured it would be a typical tech support non response but they were right on the ball.

---

### Post by angellika on 2009-11-18
> **Dude-PWB- said:**
> I just went through this with my rtl8192e chipset in my toshiba L500 laptop.

What i did was went to realtek's website and sent an e-mail to their tech support kindly asking them if they had any linux native drivers for my wireless. To my surprise, a few hours later they e-mailed me back with a driver attached.

It was an older driver and wouldn't compile in karmic with the newer kernel, so I e-mailed them again with a list of my compile errors and the next day they e-mailed me again with a newer driver, and it's working like a charm right now.

Send their tech support an e-mail with your install version, kernel version, and tell them you have the 8187se wireless chipset and see if they get back to you. I was pleasantly surprised, I figured it would be a typical tech support non response but they were right on the ball.

Thanks for help  :7

I wrote to the Reatlek and they sad that driver for my kernel 2.6.31 is not ready yet. So I have to wait to be ready .o0

---

### Post by Tukusej's Sirs on 2009-12-29
can anyone send me the email of toshiba tech support? cos i can't find it ...

---

### Post by qwerty123321 on 2009-12-31
I have the same card and need help getting it t owork!!

---

### Post by qwerty123321 on 2010-01-01
bump..

---

