---
title: "New wireless router"
date: 2012-05-12
forum: Networking &amp; Wireless
---

### Post by Jon Anderson on 2012-05-12
I'm getting a Sagem F@st 1704  router and it says it has a CD to install this router, is that going to work in Linux. The example says the cd will install in different window programs.

---

### Post by Enigmapond on 2012-05-12
No it probably won't but normally the CD it just a program that helps you set it up. If you know how to set up the network then it won't matter. It probably has a web interface you can connect to by just typing 192.168.1.1 in the browser.

---

### Post by Jon Anderson on 2012-05-12
> **Enigmapond said:**
> No it probably won't but normally the CD it just a program that helps you set it up. If you know how to set up the network then it won't matter. It probably has a web interface you can connect to by just typing 192.168.1.1 in the browser.
Thanks for the quick reply ,I have never set a router OR NETWORK up in linux(ubuntu12.04) Any sugestions

---

### Post by Enigmapond on 2012-05-12
Are you setting up an inhouse network or is it just for your box to the net?

---

### Post by Bucky Ball on 2012-05-12
Pretty straightforward and will be easier when you have the router and are in the process of setting it up. Then we can help more specifically. 

As mentioned, you open a browser, type the IP of the router in the address bar (may be 192.168.1.1 but they can vary; the defaults for mine, for instance, were 192.168.0.1). That will open the router configuration and just follow your nose. But we can help you with this bit. 

You should do all this with the computer plugged directly into the router with a cable, don't bother about plugging the modem into the router for now. You want to set up the router so it is happening with your local machine (LAN). Once this is happening, plug in the modem (WAN side) and set that up. 

You don't need the install CD for any of this. You just need to plug an ethernet cable between the two devices and switch 'em on. ;)

---

### Post by Jon Anderson on 2012-05-12
> **Bucky Ball said:**
> Pretty straightforward and will be easier when you have the router and are in the process of setting it up. Then we can help more specifically. 

As mentioned, you open a browser, type the IP of the router in the address bar (may be 192.168.1.1 but they can vary; the defaults for mine, for instance, were 192.168.0.1). That will open the router configuration and just follow your nose. But we can help you with this bit. 

You should do all this with the computer plugged directly into the router with a cable, don't bother about plugging the modem into the router for now. You want to set up the router so it is happening with your local machine (LAN). Once this is happening, plug in the modem (WAN side) and set that up. 

You don't need the install CD for any of this. You just need to plug an ethernet cable between the two devices and switch 'em on. ;)
***********************************Thanks for the quick reply, I will be wiring from my computer to the Sagem fast 1704, I will connect another computer directly to the router but I will be going wireless to Roku2 which will be connected to the TV

---

### Post by Bucky Ball on 2012-05-12
Cool. Set up the router with one computer plugged in via cable to configure the router, nothing else. Keep it simple. 

Once that is good to go (and you know all is working with the 'config' computer; it's communicating with the router and the router and computer are online), plug the next device into the router and set that up - one device at a time, don't plug 'em all in at once to avoid confusion. 

Things should then start to fall into place. Leave the wireless device until last as this is a slightly different setup. You will need to input security config to the router and set the Roku2 up with a static IP address, if it hasn't already got one ... ;)

We have four computers, wireless printer and hard drive recorder; all have static IP addresses. It makes it easier to locate them on your local area network (LAN). For guests who come with computers and want to join our LAN, I have the router serving IP addresses in the range 192.168.0.10 - 20 via DHCP . My local static IP addresses are set outside this range, naturally.

Probably too much info but you'll know what I mean when you get there! When do you get this beast?

---

### Post by Enigmapond on 2012-05-12
> **Bucky Ball said:**
> Cool. Set up the router with one computer plugged in via cable to configure the router, nothing else. Keep it simple. 

Once that is good to go (and you know all is working with the 'config' computer; it's communicating with the router and the router and computer are online), plug the next device into the router and set that up - one device at a time, don't plug 'em all in at once to avoid confusion. 

Things should then start to fall into place. Leave the wireless device until last as this is a slightly different setup. You will need to input security config to the router and set the Roku2 up with a static IP address, if it hasn't already got one ... ;)

We have four computers, wireless printer and hard drive recorder; all have static IP addresses. It makes it easier to locate them on your local area network (LAN). For guests who come with computers and want to join the wireless network, I let the router serve IP address via DHCP in the range 192.168.0.10 - 20. My local static IP addresses are set outside this range, naturally.

Probably too much info but you'll know what I mean when you get there! When do you get this beast?

:lolflag: Yep...what he said!..:)):P

---

### Post by Jon Anderson on 2012-05-12
> **Enigmapond said:**
> :lolflag: Yep...what he said!..:)):P

It was all shipped a couple of days ago both the routor and the Roku. Now I'm looking into a antennas

---

