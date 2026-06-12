---
title: "WEP problems helpss!"
date: 2009-01-10
forum: Networking &amp; Wireless
---

### Post by the4thwall on 2009-01-10
Okay, recently three things have happened. I have bought a new laptop, meaning I took out my desktop harddrive and am using it as an external. Recently I bought a new hd, and am using it on my desktop, I also got a new modem. 

Here's the problem:

This new modem has WEP key. Now with the old modem, my wifi on ubuntu would pick it up, and connect. Now I have reinstalled Ubuntu, it picks it up, but does not work with my WEP key. I am using the same key I use for my wireless laptop, it just refuses to connect. 

A little more history. Originally I installed newest version of ubuntu (I think its 8.10). It would connect to the internet, but for some reason, very slowly. So I figured I would use a version which I've always known has worked, 7.10 and 7.04. Nope, at least 8.10 connected, badly but still connected. Mind you it picks up signals, it just doesn't connect.

---

### Post by x22 on 2009-01-10
welcome to the forum

here's the script I use with our WEP enabled
router: the two "key" lines are the ones

# iwlist wlan5 scan 1>/dev/null
ifconfig wlan5 up
iwconfig wlan5 essid esa
iwconfig wlan5 mode managed
iwconfig wlan5 channel 6
iwconfig wlan5 key 1234567890
iwconfig wlan5 key open
dhclient wlan5

works fine

---

### Post by the4thwall on 2009-01-10
Well, there are no computers handling the router, so I just modified that code for wifi0 (my wireless connector), it said Operation not permitted

---

### Post by sp0nge on 2009-01-10
Consider [WPA]("http://www.home-wlan.com/WEP-vs-WPA.html")?

In addition, confirm that the NIC supports the security type. I once encountered a NetGear card that just didn't support WPA. The choice becomes changing the security type or changing the hardware.

---

