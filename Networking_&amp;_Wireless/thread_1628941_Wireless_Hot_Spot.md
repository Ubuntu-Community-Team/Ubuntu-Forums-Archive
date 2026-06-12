---
title: "Wireless Hot Spot"
date: 2010-11-23
forum: Networking &amp; Wireless
---

### Post by gmgdnj on 2010-11-23
Hello,
 
I need to make a wirelss Hot Spot at our small hotel in Italy. I am already doing it, however I have no way of logging my customers. As per the new laws here in Italy, I must secure my wi-fi and keep a log/database of all that enter. I have found some units that will cost me about a 1000euro to purchase, but I am providing this to my customers for free, so if I can do this by using one of my extra/old computers running linux, that would be ideal.
 
I did a general search for these terms: "wireless access point hot spot firewall"
but there were zero results, which I thought was strange.
 
Anyway, if anyone can help me out here, I would greatly appreciate it. 
 
Gregg

---

### Post by grahammechanical on 2010-11-23
There are three parts to this problem. 1) setting up a wireless access point. 2) logging those that access the wireless access point. 3) securing the wireless transmissions between computers and the access point.

This link may help with point 1

[]("https://help.unbuntu.com/community/WifiDocs/WirelessAccessPoint")[https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint](https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint)


I have not read it myself

Regards

---

### Post by grahammechanical on 2010-11-23
I have been doing a little research and thinking about your request. I would suggest that the server edition of Ubuntu would be better for you than the desktop edition. It may contain programs that are more suitable and not available in the desktop edition.

You need to think seriously about the router/modem that you will use and also the wireless network card that you install into the PC that will act as an access point.

You may also want to investigate something called WPS. Wireless Protected Setup. It makes it possible for wireless access through the Wireless Access Point to be secure (encrypted). If you allow open access then anyone within range can use your wireless connection and also "listen in" on the transmissions of your customers (not a very good service).

WPS is a way of giving access to a secured wireless network without giving out the password. The wireless router must be able to support this. From my investigations, if the router supports WPS it should be possible to press a button on the router to allow a wireless connection to the router without the password being given out. The other way is to give out a PIN (Personal Identification Number).

I do not know how to do these things. I do not have any experience in this. I have learnt a little about this by trying to educate myself to help on this forum.

Regards.

---

### Post by gmgdnj on 2010-11-23
Thanks Graham. I will look into the server edition. More than likely it will include what I need. I had done this before using Win2000 as a internet gateway box for our customers about 8 yrs ago. Back then I did not have to log or track though. I was doing it more for the experience and such.
 
I am already setup as a hot spot, infrastructure completely covers the premises, all WPS AP's, plus to keep the strays out of our parking lot I set up an access key. But like I said, the law here requires the logging and tracking of sites of usage, antiterrorismo is what they call it. So essentially, I am missing item (2)
 
>  grahammechanical: There are three parts to this problem. 1) setting up a wireless access point. 2) logging those that access the wireless access point. 3) securing the wireless transmissions between computers and the access point.
 
Thanks again

---

### Post by gmgdnj on 2010-11-23
Taking a quick look at that link, looks as I did it with Win 2000.  I am sure I can figure out how to make a logging, unless someone already has something created.... ;) :p

---

### Post by bitscarre on 2010-11-23
Look at some of the Linux distros which are firewalls, eg: redwall, smoothwall etc. etc.
The advantage of using one of those distros is that they are aimed at logging, filtering and restricting everything you need them to.

It would be possible to run one in a headless virtualbox with dhcp activated for the clients to get an ip from it. One of these setups would give you everything you need. Some will say that this setup is risky, but there is no hard proof for that. You have been warned though.

I find it to be quite tricky to get a wireless access point to work in some conditions(need specific wifi card, it's tricky with some new updates sometimes) so my advice is to get a computer with 2 Ethernet nics, and a wifi access point separately. With this hardware you'll be saving yourself from a lot of trouble. 

As for the electricity, you can get some really low power computers these days to serve your purpose. See the via mini motherboards or the nettops available. I assume you aim at cutting costs especially if it's for free Internet so a computer using 10W should be just perfect.

---

### Post by gmgdnj on 2010-11-24
> **bitscarre said:**
> I find it to be quite tricky to get a wireless access point to work in some conditions(need specific wifi card, it's tricky with some new updates sometimes) so my advice is to get a computer with 2 Ethernet nics, and a wifi access point separately. With this hardware you'll be saving yourself from a lot of trouble. 
 
 
This is essentially what I was looking at doing.  I will look into those other distros thanks.  I had no knowledge that there were specific distros for this type of situation, I figured there would be just did not know about them.
 
Gregg

---

### Post by bitscarre on 2010-11-24
I'm glad I managed to point you in the right direction. I have been trying to do something similar for a few weeks and I barely managed to get it to work the way I want it to without fail and dirty patches.

Good luck and share everything you find on this topic :D

---

