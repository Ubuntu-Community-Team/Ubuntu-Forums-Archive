---
title: "Problems with Comcast Xfinity wireless"
date: 2012-12-09
forum: Networking &amp; Wireless
---

### Post by morven on 2012-12-09
I have a Sony Vaio SVE17122CXB with an Atheros AR9485WB-EG wireless chipset that is having severe problems connecting to a Comcast Xfinity wifi access point under Ubuntu 12.10.  I have not tried other versions or distributions.

It works fine with other wireless networks; I've used it in coffeehouses etc. with no complaints.  The wireless works fine in Windows.

The Xfinity is using WPA2 security with AES encryption.

Googling answers turns up lots of cases where the problem turned out to be in DNS.  This is not one of those.  

Symptoms here: Ubuntu connects to the access point seemingly successfully and shows an established connection.  It gets DHCP results that are correct (identical to the working Windows connection). 

However, it does not successfully communicate with anything.  Pinging the gateway (the Xfinity) gets one ping reply about every hundred pings.  Pinging anything outside gets nothing.

Any ideas?

---

### Post by ulfj on 2012-12-09
I will be watching this thread aS i seem to have the same problem, I connect to the access point just fine but to get to my home page I have to restart my machine then I can search but click on a link and all I get is "server not found"
   This only happens on residentual access points all otthers are fine.

---

### Post by EmmEight on 2012-12-09
Ditch the xfinity router? 

I have never had much luck with a router/gateway all in one solution.

Open up a terminal and run [CODEifconfig[/CODE]

Then open up a browser and type your ip address, but replace the last octect with a 1

192.168.1.7 -- Your local ip
192.168.1.1 -- Type this into a browser

If I remember correctly comcasts default username is admin and the password is highspeed

you can always google your default credentials

I would suggest skimming through the web client program for any oddities, and if all else fails change the DHCP IP handout scheme

?):P

---

### Post by EmmEight on 2012-12-09
Yeah Comcast isn't the best...

What speeds are we getting in Pb-ville?

):P

---

### Post by morven on 2012-12-09
I solved it!  It was set to WPA2 with TKIP/AES encryption.  I forced it to choose TKIP and everything began to work.

Still had the oft-reported issue with dnsmasq, but that was easily fixed.  

Didn't try whether forcing AES would also work.

---

