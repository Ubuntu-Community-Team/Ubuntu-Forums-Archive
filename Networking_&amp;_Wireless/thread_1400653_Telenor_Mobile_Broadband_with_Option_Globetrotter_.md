---
title: "Telenor Mobile Broadband with Option Globetrotter GI0505"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by trommas2 on 2010-02-07
Hi!

I've been trying to set this up for ages, following 20+ guides. I'm running ubuntu 9.10 with the latest networkmanager (from ppa)

I plug in the usbmodem and it's picked up nicely (from kernel.log):

```
usb 1-1: new high speed USB device using ehci_hcd and address 3
...kernel: [  105.365942] usb 1-1: configuration #1 chosen from 1 choice
...kernel: [  106.538198] usb 1-1: USB disconnect, address 3
...kernel: [  106.812228] usb 1-1: new high speed USB device using ehci_hcd and address 4
...kernel: [  106.950794] usb 1-1: configuration #1 chosen from 1 choice
...kernel: [  107.563963] hso: /build/buildd/linux-2.6.31/drivers/net/usb/hso.c: 1.2 Option Wireless
...kernel: [  107.567020] hso0: Disabled Privacy Extensions
...kernel: [  107.569073] usbcore: registered new interface driver hso
...kernel: [  107.617001] Initializing USB Mass Storage driver...
...kernel: [  107.617319] usbcore: registered new interface driver usb-storage
...kernel: [  107.617334] USB Mass Storage support registered.
```The connection is listed in NetworkManager, it tries to connect but fails after 3 sec.

I thought this could be wrong credentials setting, so i've tried a huge amount of setups (user: phonenumber, password: phonenumber, avp:telenor, seems to be the general consensus for how it should be)

Is there something I'm missing or is there any way I could tail the output as NetworkManager tries to connect (hopefully seeing something like "wrong password" etc.)

---

### Post by trommas2 on 2010-02-08
I'm using ubuntu netbook remix, if that matters...

---

### Post by trommas2 on 2010-02-08
Well, seems like this may be to specific to get some help on.. But does anyone know how to print output from NetworkManager? (or perhaps Modemmanager is the one in use?)

---

### Post by alexfish on 2010-02-08
hi

here are some links worth reading

  	 	 	 	 	 	  [http://ubuntuforums.org/showthread.php?t=49056](http://ubuntuforums.org/showthread.php?t=49056)
 
  	 	 	 	 	 	  [http://www.pcurtis.com/ubuntu-mobile.htm](http://www.pcurtis.com/ubuntu-mobile.htm)
[URL="http://www.pcurtis.com/ubuntu-mobile.htm"]
[/URL]
 [http://www.pharscape.org/](http://www.pharscape.org/)

---

### Post by trommas2 on 2010-02-16
Thanks!

Those where useful pointers. 

Seems it is possible to get working on kernels below 2.6.30 :(

Just my luck...

---

### Post by lasjen on 2010-05-07
Don't know if you got it working, but I spent about 15 minuttes to get my working.
Downloaded and installed the following two packages:
 
ozerocdoff_0.4-2
vodafone-mobile-connect_2.25.01-1_all.deb
 
Which i found:
[https://forge.betavine.net/frs/?group_id=12&release_id=272](https://forge.betavine.net/frs/?group_id=12&release_id=272)
 
Then it was just to open the "Vodafone Mobile Connect" under "Programs->Internet", set the phone number towards Telenor, username=Telenor, Password=<pin>, and suddenly I was on.
 
Cheers,
Lasse

---

### Post by pdc on 2010-05-07
well done;

looking back to Feb, I think that when trommas2 got 

> USB Mass Storage support registered.

...... and thought he was cooking with gas ........ that was a bit premature ........

you did the right thing with option to use ozerocdoff and flip the device .. option seems to mean ozerocdoff ...........

good work;

and interesting that vmc is working too; they had ubuntu 9.10 problems and were unhappy then

---

