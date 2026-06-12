---
title: "Anyone got success with a Belkin Pre-N router"
date: 2006-07-02
forum: Networking &amp; Wireless
---

### Post by water on 2006-07-02
I've got an  [Belkin Pre-N ]("http://catalog.belkin.com/IWCatProductPage.process?Merchant_Id=&Product_Id=184316")[router]("http://catalog.belkin.com/IWCatProductPage.process?Merchant_Id=&Product_Id=184316") that I simply cannot connect to.

Before I go into a posting spree with tons of logs that I have no idea whatsover really tell you experts I'd like to know if there's anyone out there than have actually been able to connect wireless to one of the routers.

My goal is to connet to it using wpa-psk and get dhcp from my ClarkConnect box that it's hooked up with.

So the million dollar question, anybody successfully connected to a Belkin Pre-N router with Dapper?

:water

---

### Post by timrichardson on 2006-07-03
No. I have a Belkin pre-n wireless card, and I can get it to associate with my Belkin pre-n router, but DHCP (dhclient) fails. However, a static IP address also fails so my problem may not be the router but my wireless card.

---

### Post by Jason_25 on 2006-07-03
I have 2 of them at different locations.  They work great.  Both with WPA.  The Pre-N cards do not work.

---

### Post by timrichardson on 2006-07-03
I have got my pre-n card to the point where I can associate it with the pre-n router: I get signal strength readings, for example. But dhclient fails with bogus udp packet length messages. I am stuck.
Note: if I disable WEP security I can't get it to associate.

---

### Post by timrichardson on 2006-07-04
I put a Netgear 54MB/s card into the machine (atheros chipset).
It worked painlessly. So there is some problem getting the Belkin pre-n card to talk to a Belkin pre-n router using the Netgear netani driver via ndiswrapper. Looks like the router expects a Belkin pre-n card to behave in some manner that  is not supported by the Netgear driver. 

As a test, I tried to force the belkin card to 11MB/s mode but I was not successful.

---

### Post by timrichardson on 2006-07-04
.... which means that my answer to the original post is "yes, successfully connected to a Belkin pre-n router with 128bit WEP".

---

### Post by water on 2006-07-05
[quote=Jason_25]I have 2 of them at different locations.  They work great.  Both with WPA.  The Pre-N cards do not work.[/quote] 
have you done any special configuration to connect to the pre-n's with wpa or did it work out of the box with a vanilla dapper intallation?

:water

---

### Post by afoglia on 2006-07-06
I have the exact same problem.  I'm trying to connect to a Belkin pre-N router with a 802.11b card (Orinoco Class Gold PC Card).  No wep, no wpa, just completely open.  I've had no luck.

Interestingly, I can connect fine to the router when the same card is my debian stable laptop.

---

### Post by water on 2006-07-10
Hopefully I'll get the chance to do a complete reinstall later this week and find out if that can solve this issue.

I would really prefere not to have to install an aditional wap - I need the Belkin for the pre-n speed it provides to the windows boxes.

:water

---

### Post by totally wired on 2006-07-11
I've been going crazy trying to get this to work. I have an old USB 802.11b card that sees the essid, but tells me my link quality is always 2 or 3 out of 100 and cannot connect via dhcp or static adressess. Does this seem like a hardware or config issue?

---

### Post by water on 2006-08-09
I've just done a complete reinstall - and got it to work after changing the encryption to AES on the router.

The problem I've got now is that when I try changing the pre-shared key on the router the connection times out, I'm not promted for the new pre-shared key

Any ideas?

:water

---

### Post by afoglia on 2006-08-21
I'm glad someone had luck.  I'm still having no luck.  In the meantime, I replaced the hard drive and did a new Dapper install.  No change.  My Orinoco 802.11b still won't connect to the Belkin router.  And I upgraded the kernel on my Debian-stable box to 2.6.8 (was running 2.4 before).  Also no change.  In that case the card does connect to the router.

---

