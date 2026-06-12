---
title: "Wanted: USB wireless dongle that works 'out of the box'"
date: 2009-10-04
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2009-10-04
Hi all,

As the title of the post suggests.

My wireless card just died on me. Looking for a wireless dongle that will work 'out of the box', good range and doesn't gobble laptop resources. 

Have two D-Link routers that have been great so would support them but their website says nothing about their dongles being Linux compatible. 

Any and all suggestions and testimonials good/bad welcome. Using 8.04.

---

### Post by jimmers on 2009-10-04
Hi,
The one that worked for me was Vodafone, model Hauwei K3565, went online to bettavine, and downloaded the following files:-
0zerocdoff_0.4.2_i386.deb
usb-modeswitch_0.9.7_i386.deb
vodafone-mobile-connect_svn20090615_all.deb
After installation works just great.

I am using Jaunty

Good Luck

Jimmers

---

### Post by Bucky Ball on 2009-10-04
Thanks Jimmers. I am looking for a dongle to connect to my LAN at home, already have a cable deal. Are you thinking a wireless account? Na, just the dongle.

The one I have been looking at is here:

[http://www.tp-link.com/products/product_des.asp?id=47](http://www.tp-link.com/products/product_des.asp?id=47)

Doesn't say much about the range as in distance though. I did a build at Christmas and used one of their cards and it definitely worked 'out of the box'.

---

### Post by freechiru on 2009-10-04
I can't help, but I'm registering my interest in any answers to this thread! (:

---

### Post by tigang on 2009-10-09
I am simply going MADDDDDDDD trying to get a [reasonably priced] USB wireless adapter that will work without NDISWrapper etc. This has got to be THE most difficult transition to Linux element EVER!!

My IBM laptop WiFi configured 'out of the box' but my mate who I have recently converted to Ubuntu has a laptop without indigenous WiFi and hence the requirement for a USB stick.

Tried 4 so far and USELESS!

My latest try was to pop into PCWorld on my way home today and pick up a 'safe bet' BELKIN 7050... Ubuntu Karmic says... NO!

I hate to say this but... Windoz$$$$$$$ beats this aspect of Linux hands down. Let's face it... the 'Uni crowd' are not going to run with Linux unless WiFi gets a lot easier!

---

### Post by Bucky Ball on 2009-10-09
A lot of the TP-Link cards and dongles work out of the box even though their website gives little suggestion of them working with Linux at all.

---

### Post by ian920 on 2009-10-09
Wireless? Arghhh I need help in this department myself.  I'll wait and see ](*,)

---

### Post by Cam42 on 2009-10-09
I've had high, high levels of success with my Belkin USB dongles. Even though they don't "support" linux, mine work excellently with Ubuntu. Model #F5D7050 Is what I use. No experience with any others.

---

### Post by davemar on 2009-10-27
Did you have to install anything to get the Belkin dongles working? Which models of the dongles have you had success with?

---

### Post by Bucky Ball on 2009-10-27
> **Cam42 said:**
>  Model #F5D7050 Is what I use. No experience with any others.

Davemar, it's written right there.

---

### Post by shaggy999 on 2009-10-27
You did not state which wireless spectrum you were going for (a/b/g/n), but here's a link to a b/g adapter that everyone states works perfectly with the linux driver built into the kernel:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833129080](http://www.newegg.com/Product/Product.aspx?Item=N82E16833129080)

Apparently it's plug-n-play with just about every version of linux as long as the $kernel_version > 2.6.24.24 which is true as of several releases of ubuntu ago, I think it's been in ubuntu since 8.04. Also, it supports the latest WPA2 encryption.

---

### Post by Bucky Ball on 2009-10-28
Thanks for the input all. I will probably be going for the [Edimax USB 7316UG]("http://www.edimax.com/en/produce_detail.php?pd_id=258&pl1_id=1&pl2_id=44"). If anyone has any experiences to relate about these wireless dongles please let me know. Probably get it on the weekend.

The Edimax website claims Linux compatability and I can get one in Australia for a cheap and nasty AU$12. Sounds good to me. Let you know how I go.

---

### Post by Cuba71 on 2009-10-28
I own both of these USB adapters, tested to work out of the box with Ubuntu 9.4 and 9.10.  But I know Belkin make different adapters under the same model name.
I got both from eBay for under $15 each.

```

Belkin F5D7050A USB  Wireless Adapter
ID: 050d:705a
Linux Driver:  RT73

D-Link DWL-G122 USB Wireless Adapter
ID: 07d1:3c03
Linux Driver:  RT73

```

---

### Post by Onesimus on 2009-10-28
I use a Wireless Lan usb 2.0 adapter (54Mbps)  Sweex LW053.  It supports 802.11b/g  WPA/WEP, TKIP/AES encryption.  

I needed to use ndiswrapper using jaunty, but it works out of the box for karmic.

it seems that there is better support for wireless in karmic.

---

### Post by Bucky Ball on 2009-10-28
I use 8.04 because I need my machines to be up ALWAYS. Wireless support is excellent for everything I've tried setting up and building other people's boxes. I refuse to use ndiswrapper!

I'll have a look for Sweex. Never heard of them here.

---

### Post by pdc on 2009-10-28
I found the Dick Smith USB adapter works well; 

available from any Dick Store store in Australasia

[http://ubuntuforums.org/showthread.php?t=1281183&highlight=dick+smith+usb](http://ubuntuforums.org/showthread.php?t=1281183&highlight=dick+smith+usb)

I described what I did to configure it in the above post; 

I understand it is b/g

I have been pleased with it

---

### Post by shaggy999 on 2009-10-29
> **pdc said:**
> I found the Dick Smith USB adapter works well; 

available from any Dick Store store in Australasia

[http://ubuntuforums.org/showthread.php?t=1281183&highlight=dick+smith+usb](http://ubuntuforums.org/showthread.php?t=1281183&highlight=dick+smith+usb)

I described what I did to configure it in the above post; 

I understand it is b/g

I have been pleased with it

Worst name for a USB adapter ever. Same goes for the store.

---

### Post by Bucky Ball on 2009-10-30
> **shaggy999 said:**
> Worst name for a USB adapter ever. Same goes for the store.

Sorry about that shaggy. We think Dick Smith is a classic name! It's a real person and he is a bit of an Australian icon (he has actually been name an Australian Living Treasure). The store is called Dick Smith's, not Dick Store, although that would be hilarious if it was the latter! 

His grocery chain does sell matches called Dickheads though! We have a brand here called Redheads and it is a pun on that I guess, as well as just being an Australianism if there is such a word (well there is now!). Check him out; first person to fly solo round the world in a helicopter. Fascinating guy and the doco(s) of him doing it are interesting too:

[http://en.wikipedia.org/wiki/Dick_Smith_(entrepreneur]("http://en.wikipedia.org/wiki/Dick_Smith_%28entrepreneur"))

Thanks for the tip pdc

---

### Post by ozziearsenal on 2012-07-16
Check out  [www.cyberciti.biz/tips/linux-usb-wireless-compatibility-adaptor-list.html](www.cyberciti.biz/tips/linux-usb-wireless-compatibility-adaptor-list.html)
this guy has tested quit a few and will answer your needs have a look regards joe

---

### Post by Hadaka on 2012-07-16
Hawking HWUG1 usb wireless...works out of the box,no software to load,
no files to tweak...100% plug and play.  At least this has been my experience
on 4 different Dell laptops. By default the Hawking uses the RT73 usb driver.
works no problem with ubuntu 11.10 and 12.4 Lts

hope this helps.

---

### Post by Hadaka on 2012-07-16
just noticed...this is an ancient thread...

---

