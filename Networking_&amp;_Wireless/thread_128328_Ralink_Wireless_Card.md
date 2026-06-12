---
title: "Ralink Wireless Card"
date: 2006-02-11
forum: Networking &amp; Wireless
---

### Post by PriceChild on 2006-02-11
Hey all,

My wireless networking PCI card has been detected during the install, but i've decided i want to do something with it :P

In the networking admin, it allows me to make a network etc. but how can i actually search for a network and connect to it?

I've got the Linux source for the card from ralinktech.com (RT2500-Linux-STA-1.4.6.2.tar.gz) But aren't quite confident enough to use it. Does this actually need to be used?

I bet you lot have got something better for me lol.

Any advice would be very gladly received, Pricey

---

### Post by Jimmey on 2006-02-11
Well, there's wifi radar, in the Ubutu repositories ( that's assuming that you can access at least one wireless network. )

Here's a link, just in case: 
[http://www.bitbuilder.com/wifi_radar/]("http://www.bitbuilder.com/wifi_radar/")
Hope that helps.

---

### Post by UbuntuLinuxUser on 2006-02-12
nice, now if I can just get my wireless card to work, I'd be good....

---

### Post by Jimmey on 2006-02-12
Does the interface "ra0" appear when you navigate through "System >> Administraion >> Networking" ? My Ralink worked, straight away.

---

### Post by PriceChild on 2006-02-12
Yeah ra0 appears... so i can just use it straight from there? seems a bit wierd though cuz i can't search for other networks and connect from there?

---

### Post by Jimmey on 2006-02-13
That means that you don't need the divers for it - It's already got the appropriate drivers installed. What you need to do now is configure it. It's not that hard..Mainly, you've just got to enable it, and set it as the default device. Then, once you have the internet, download wifi radar, which scans for available wireless networks that you can connect to.

---

### Post by PriceChild on 2006-02-13
had a bit of an experiment with wifi radar.... seemed a bit slow to connect to networks etc.

What about GTK wifi?

---

### Post by Jimmey on 2006-02-13
I've never had any experience with it, and so I can't say :P

---

