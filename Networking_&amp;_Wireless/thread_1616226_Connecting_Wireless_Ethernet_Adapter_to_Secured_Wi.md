---
title: "Connecting Wireless Ethernet Adapter to Secured Wireless Router"
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by TripleOnyx on 2010-11-07
I have an Ethernet wireless adapter. It connects to my computer by Ethernet but it gets a wireless signal to gain internet access wirelessly. I need help to configure this kind of wireless adapter as my wireless network is secured. 

I am very new to Ubuntu so I need someone who can provide some detailed steps for me to accomplish this.

---

### Post by uncaspi on 2010-11-08
I don't know if I understand what you mean, but try to right click the network icon in upper panel and choose Edit connections. Here you can apply a key to your wireless card. I suppose it is eth1.

---

### Post by chili555 on 2010-11-08
Welcome to Ubuntu! We are glad to see you and we'll do our best to help you.

The first step is to make sure your wireless adapter has a driver associated with it. Click the Network Manager icon at the top right of your desktop and see if you can see wireless networks listed like in the attached.

If Wireless Networks is greyed out and no networks are available, then you probably need to find and install a driver for your wireless card. Let's ask your computer to tell us what it needs. We are going to use the terminal because it is the fastest, easiest way to get information. We will be entering commands and learning the result when we press 'Enter.' Here is an example. If I ask you to do:```
lscpi -nn
```You will enter that on one line in the terminal and press enter. As an example, here is the result from my computer:> 03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)I cut away everything that wasn't my wireless card; if you are in doubt, post everything.

Is your wireless adapter built-in or USB? If it is built-in, please open Applications > Accessories > Terminal and do:```
lspci -nn
```Post the part related to your wireless. If it's USB, please do:```
lsusb
```Post the result, and we'll proceed.

Incidently, the encryption part is the easiest thing we have to do! Network Manager will determine that your network is encrypted and ask you for your password. If you give the correct password, it will connect. You can also set Network Manager to connect automatically.

I look forward to your reply.

---

### Post by dforthman on 2010-11-08
I think he's talking about something similar to (if not) this:
[http://www.amazon.com/D-Link-DWL-G810-Ethernet-Wireless-Adapter/dp/B0000CEPCH](http://www.amazon.com/D-Link-DWL-G810-Ethernet-Wireless-Adapter/dp/B0000CEPCH)

A wireless device that plugs in to a NIC.

It says "No Driver Needed" so I assume there is a built-in setup you can access similar to a router's setup page. You will need to find the documentation that came with the device to find out how to log in and set up the wireless encryption.

---

### Post by chili555 on 2010-11-08
Ahh! Perhaps so. Is that it, TrpleOnyx?

I have used a wireless bridge before and they're not too difficult. I am sure we can find the manual on line.

BTW, dforthman, I can see Charlotte across the lake! Wave to me.

---

### Post by dforthman on 2010-11-08
Actually, I'm at work in Indian Land, SC right now.

---

### Post by TripleOnyx on 2010-11-08
Yes that is it. A wireless bridge. I thought all wireless bridges work the same. I hope I still have the documentation. 

brb :)

---

### Post by chili555 on 2010-11-08
They all do work essentially the same. You must set up the bridge to use the same encryption as the router; that is WEP, WPA or WPA2. You must also supply the password.

If you can supply the make and model, we can probably find the manual on line and help you out.

Your computer hooks to the bridge by ethernet cable. As far as your computer is concerned it is a wired ethernet connection.

---

