---
title: "w-lan security!"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by artheus on 2009-07-04
Hi!

I recently took a trip with a cruiseship. And on that cruiseship was a wireless internet connection. I tried to log on at first. And that seemed painlessly simple.. But when I then entered my web-browser I got a log in screen. Whatever adress I entered, I still got the log in screen.

And I fell in love with that function! :D

I now really want to know what procedure I have to go through to get that same function on my w-lan at home.

How to set up my network, so my Ubuntu Server can log every attempt, and all the traffic shall go through my server.
And the first thing everyone sees as they log on to my wireless network, is my log in screen.


How can I do this??

Cheers,
Artheus

---

### Post by Boondoklife on 2009-07-04
Well I think one could achieve this by running a proxy on the server and having all traffic go through it. But there are real issues with that setup, read more [here]("http://www.mail-archive.com/squid-users@squid-cache.org/msg51232.html")

And [here]("http://wiki.squid-cache.org/Features/Authentication?action=show&redirect=SquidFaq%2FProxyAuthentication") is another good squid faq for authing

---

### Post by artheus on 2009-07-05
thanks for that!

The thing is that what I wanted to achieve with this wast extra protection.. but if it causes securityholes I don't want this..

Well.. I wanted to have this in addition to a hidden WLAN ID and a WPA-Personal PSK protection.. **Are there still security holes then?**

Cheers,
Artheus

---

### Post by Boondoklife on 2009-07-05
Well the same issues would persist if the user was able to get your ssid and psk as they are still on the network. One of the issues is just an issue of IP cloning.

I think a more valid option would be a very strong password for the PSK

---

