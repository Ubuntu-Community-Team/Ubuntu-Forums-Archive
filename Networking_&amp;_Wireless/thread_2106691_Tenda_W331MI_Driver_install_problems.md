---
title: "Tenda W331MI Driver install problems"
date: 2013-01-19
forum: Networking &amp; Wireless
---

### Post by J4cksburgers on 2013-01-19
Hi there,
I recently bought a pc and installed ubuntu 12.10. it came with a wireless usb adapter (model no. in the title) and the driver disk, but i have no idea how to install the driver. i have a .bz2 file and i need to kow how to install it as i have no clue where to go from here.

Any and all help appriciated!

---

### Post by lesmey on 2013-01-19
I have a Tenda W322U USB stick and did not need to install a driver for it to work (just plug and play)

---

### Post by ahallubuntu on 2013-01-19
> **J4cksburgers said:**
> Hi there,
I recently bought a pc and installed ubuntu 12.10. it came with a wireless usb adapter (model no. in the title) and the driver disk, but i have no idea how to install the driver. i have a .bz2 file and i need to kow how to install it as i have no clue where to go from here.

Any and all help appriciated!

A bz2 file is a compressed file - you can open a terminal and type:

```
bunzip2 FILENAME.bz2
```

If there's a ".tar" at the end before the ".bz2" try tar instead:

```
tar xvf FILENAME.tar.bz2
```

which will probably create a directory you can cd into and look for a way to build it.

You could also grab the latest driver from Tenda's website:

[http://www.tenda.cn/tendacn/DownLoads/show.aspx?downid=912](http://www.tenda.cn/tendacn/DownLoads/show.aspx?downid=912)

Looks like it's a Ralink chipset.

---

### Post by Bucky Ball on 2013-01-19
Welcome to the forums. 

Just plug it in. Do an update. Restart. Should work. You don't need to install a driver. It is a ralink chipset but you can run 'lsusb' in a terminal to determine which. They are well supported 'out of the box'. The driver should be part of the kernel and you probably won't need to do an update/restart.

---

### Post by J4cksburgers on 2013-01-20
Thanks guys, I plugged it in and restarted my pc and it worked and is now receiving a wireless signal. 

Next problem, it won't let me access the internet for example goin to YouTube would give me message along the lines of 'this web page is not available' which is weird 'cause I can get my internet to work over a wired connection.

Again help much appreciated :D

---

### Post by Bucky Ball on 2013-01-20
You might need to right click on the network icon and just make sure you have all the right details in there, both for you ISP and for the router.

Sometimes you need to put in the DNS servers, IP addresses that will be provided by the ISP, and the gateway to get out of the LAN, e.g. the IP of your router. 

Probably that simple, but I could be wrong ...

---

