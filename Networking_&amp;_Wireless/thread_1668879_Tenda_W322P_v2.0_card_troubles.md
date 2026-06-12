---
title: "Tenda W322P v2.0 card troubles"
date: 2011-01-16
forum: Networking &amp; Wireless
---

### Post by evans62 on 2011-01-16
I was encouraged when I put this card in and it seemed to be recognized right away, but it didn't work.  Then I did some searching and found that RT2800 drivers usually load and conflict.  

So, I went thru the trouble of compiling the Linux code that came with the card, and somehow I got it to install. 

Some post said I should blacklist a bunch of rt2x00 and rt2800 drivers, and I did that.

Now, the wireless works - kind of  ;)  Just a little bit.  That is, I can see a ra0 interface in ifconfig and get it to come up.  I can do a 

sudo iwlist ra0 scan

and I can see my access point.  

But nothing else works.  It will accept these commands, but it doesn't do anything:

sudo iwconfig ra0 essid xxx
sudo iwconfig ra0 key yyy
sudo dhclient

What am I missing?

---

