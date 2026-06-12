---
title: "Help with wlan0 -&gt; eth0 connection"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by mbartoli on 2009-06-21
Hello all.
Here's the situation, Computer A has a wireless internet connection with the wlan0 interface (wired is unavailable.) Computer B does not have a wireless card, but does have a eth0 interface. I have a Cat5 Crossover cable. I need to take the connection that I'm getting on Computer A and get the connection to work on Computer B. Both computers are running Ubuntu 9.04. Any suggestions?
Thanks,
Mike

---

### Post by Iowan on 2009-06-22
Crossover cable won't help unless you have some place to plug it on Computer A.  You will either need a common connection type (wired/wireless/USB/parallel/etc.) on both computers or an adapter to convert... somehow.  I can't think what kind of adapter might work.
 Unless it's a laptop, an ethernet card for Computer A seems easiest.

---

### Post by jonobr on 2009-06-22
I reckon On your current setup with what you described, nothing can work.,

How are you connecting wireleswly?
Is it an 802.11 (wifi) connection?
If so, you really need to buy yourself a cheap linksys router, or find some way of getting a wired connection on your computer B as Iowan says

If you end up buying a connector (usb to ethernet) you may end up with driver problems and cuase your self more headaches,
In the end, if you have spare money, save yourself problems and get the wireless ap with an ethernet port you can use for comp b

---

### Post by mbartoli on 2009-06-22
Thanks!
Okay, so there is an Ethernet card for Computer B.
I set different static IP address on both computers. Is there any other step that I am missing.
Thanks again.

I'm connected wirelessly by 802.11 (wifi) on Computer A.

---

### Post by jonobr on 2009-06-22
I dont think your any further down the road.,

As far as I can see , there is no way to do what you want to do without buying some hardware that will allow the two machines operate on the same smae lan segment.

If you even manged to get A on the wired network, you may get somewhere

---

### Post by Iowan on 2009-06-22
There may be a way to connect the two via "laplink" cable... [Here]("http://tldp.org/HOWTO/PLIP-Install-HOWTO.html") is a How-To on PLIP. [This]("http://tldp.org/HOWTO/PLIP.html") is another more general PLIP mini-HowTo.

---

