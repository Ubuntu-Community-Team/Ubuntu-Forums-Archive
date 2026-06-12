---
title: "Wireless 3g At&amp;t"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by nintendopcgamer82 on 2009-06-02
Hi everyone, I'm new to this forum so hi.
Anyway, I'm also new to Ubuntu and I would like to know if there is a way to connect a at&t usb 3g adapter. I can't figure out how, and when I insert it into a normal windows pc, it detects it and installs stuff normally. I would like to know how to connect it with ubuntu. Thanks!

---

### Post by namaku0 on 2009-06-02
I have the same modem. All you need to do is configure
it from NetworkManager.

Right-click the icon > Edit Connections... > Mobile
Broadband, follow the wizard.

But, IIRC, NetworkManager should offer you to configure
the modem after you plug it on the USB port.

---

### Post by nintendopcgamer82 on 2009-06-02
thank you for replying, I did that and I still can't connect. There is nothing I cal click on to connect. On a normal windows pc, it just pops right up and I can click on connect. This is what I have:  [http://www.wireless.att.com/cell-phone-service/cell-phone-details/?device=AT%26T+USBConnect+Mercury&q_sku=sku2940237](http://www.wireless.att.com/cell-phone-service/cell-phone-details/?device=AT%26T+USBConnect+Mercury&q_sku=sku2940237). Would it work with ubuntu? And what AT&T configuration in the manager shout I use? I just use the plain AT&T one

---

### Post by namaku0 on 2009-06-03
Hmm, your modem is newer, mine is AirCard 881.
But I think it should be the same.
[http://www.cellcommatt.com/images/881U_ATT_medres.jpg](http://www.cellcommatt.com/images/881U_ATT_medres.jpg)

If you think NetworkManager doesn't work you
may want to try Gnome PPP instead. Even though
NetworkManager works fine for me, this is what
I am currently using actually.

There are four things you need to know to use
the modem with Gnome PPP:
[LIST]
[*]phone/dial number
[*]username
[*]password
[*]APN (access point)
[*]and modem device file
[/LIST]

Phone/dial number usually ***99#** or ***99***1#**. 

username and password should be straight forward,
but to set an APN you must set it as an init string.
```
at+cgdcont=1,"IP","yourAPN"
```
Add these line like in this picture: [http://www.geocities.com/faysalalfarooqui/ub7.jpg](http://www.geocities.com/faysalalfarooqui/ub7.jpg)

As for modem device, Linux kernel should finds
four new USB device ttyUSB0 to ttyUSB3. One of
them is the modem, so I think you should try it
one by one. In my case it is ttyUSB2.
Add the modem device here: [http://polishlinux.org/reviews/three_3g_modem_linux/gnome-ppp.png](http://polishlinux.org/reviews/three_3g_modem_linux/gnome-ppp.png)

You can always try to configure manually using
NetworkManager. After that you select the 
configured conection by right-clicking the
NetworkManager icon and select it (the
configured connection should be listed there).

---

### Post by nintendopcgamer82 on 2009-06-24
hmm...strange, the network manager pops right up on ubuntu 9.04, but it doesn't work on 8.10...so I got it working at least, so thanks :D

---

