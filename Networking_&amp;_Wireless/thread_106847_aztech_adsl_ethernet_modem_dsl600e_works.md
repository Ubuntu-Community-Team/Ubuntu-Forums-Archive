---
title: "aztech adsl ethernet modem dsl600e works"
date: 2005-12-21
forum: Networking &amp; Wireless
---

### Post by rajaiskandarshah on 2005-12-21
especially for malaysian streamyx users.

the aztech adsl ethernet modem dsl600e can work as a router - meaning that it can connect automatically to streamyx as soon as you turn on the modem.

connect the ethernet cable to your computer and it will automatically assign an ip address for your computer using dhcp. so no need to fiddle around with pppoe.

basic instruction:
1. turn on your modem and wait for the dsl indicator light is steady (not blinking)
2. connect the ethernet cable from the modem to your computer
3. open your browser and type 192.168.1.1 . this will access your modem's config page
4. login with username admin and password admin
5. in the quickstart type in your streamyx username and password and click on the connect button
6. if it connects successfully, click on the save settings
7. turn your modem off, then turn it on. wait for the dsl light is steady
8. from your browser, test your internet connection

additional information is available from [http://www.aztech.com/malaysia.htm](http://www.aztech.com/malaysia.htm)

---

### Post by rajaiskandarshah on 2005-12-22
additional networking settings:

1. from the top panel click System > Administration > Networking
2. in the network settings window, select the DNS tab
3. add the following DNS servers: 202.188.0.133
4. add the following DNS servers: 202.188.1.5

if you omit these settings, you will find your internet connection to be slow and subject to connection errors.

---

### Post by Jason7fd on 2006-01-31
So no need any drivers?

---

### Post by mips on 2006-01-31
[QUOTE=Jason7fd]So no need any drivers?[/QUOTE]

NO! Routers do not require drivers.

---

### Post by mansys on 2006-02-11
i`m having problems with networking. i using streamyx basic 512k & aztech dsl600e with 2 types of interfaces. the problem is how can i configure the usb connection instead of using ethernet port?

somebody plzz help me~!!

---

### Post by mips on 2006-02-11
Why do you want to use the USB port, you are making your life so much more difficult ???
If you dont have a Ethernet port you could probably pick a card up for cheap or get a secondhand one for free.

You need PPPoE with the USB device and possibly drivers.

---

### Post by mansys on 2006-02-11
1st of all tq 4 ur help.

definitely! but my router supports 2 types of interfaces : ethernet port and usb port. ethernet port attaches to windows(pc1) and the other one(usb) attaches to ubuntu(pc2). i`ve already configure the ethernet port on pc2, but still want to use usb port to pc2 as my usb hubs on pc1 full ( i only have 2 usb hubs)

i tried checked the device manager in pc2 and.. the driver for the usb router has already installed!. but in network config, i can`t add the device.

---

### Post by yimingwuzere on 2006-12-02
What if it fails to make a connection? (regarding post 1)

---

### Post by rajaiskandarshah on 2006-12-07
as you are actually configuring the the modem as a router, potential problems on why it may fail are:
1. wrong username or password (contact tmnet)
2. suspended account (contact tmnet)
3. ethernet card problem (test with another computer)

---

### Post by nesohu on 2007-03-15
> **rajaiskandarshah said:**
> additional networking settings:

1. from the top panel click System > Administration > Networking
2. in the network settings window, select the DNS tab
3. add the following DNS servers: 202.188.0.133
4. add the following DNS servers: 202.188.1.5

if you omit these settings, you will find your internet connection to be slow and subject to connection errors.
Raja, hope you can help me regarding this issue

After setting these DNS servers, I am able to connect to the net for about 15 minutes before the DNS servers are reset to 192.168.1.1 . Where do you think the problem arises?

---

### Post by rajaiskandarshah on 2007-03-16
are you connecting directly to the modem or connecting through a wireless router connected to the modem ?

---

### Post by nesohu on 2007-03-20
thanks raj, already solved the problem

-> login as root
-> perform DNS setting
-> logout
-> login as username-desktop
-> done.

---

### Post by vvy on 2007-12-30
> **rajaiskandarshah said:**
> are you connecting directly to the modem or connecting through a wireless router connected to the modem ?

Hi

I am having problems connecting to streamyx and I am using a wireless router - D-Link Airplus G+ DWL G520. Can you help please?

---

### Post by radha2g on 2008-02-12
this question is gonna sound a little weird...
will this changes affect the connection of windows XP? i know, i know... windows... yuck
but my sister doesnt like ubuntu, and the modem/router is not mine alone so i cant take that risk

---

### Post by mips on 2008-02-14
No. Just enable DHCP & Auto DNS in windows and remove the PPPoE client that you have installed.

---

