---
title: "Why is my wifi access point showing up twice?"
date: 2012-08-17
forum: Networking &amp; Wireless
---

### Post by blackdalek on 2012-08-17
Why is my wireless AP showing up as two separate wireless networks?

The connection information icon at top lists under Wireless Networks -

"my wireless network name"
plus "my wireless network name 1"

I've tried resetting the AP and restarting the computer. It still persists.

Using Ubuntu 12.04 on a laptop with Unity 2D

Wireless card in laptop is:
02:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

AP is a Billion BiPAC 7800NL ADSL2 router

---

### Post by lindsay7 on 2012-08-17
Is this a dual band router?


Dual Band Routers

Unlike ordinary routers that only support one wireless signal band, dual-band routers contain two different types of wireless radios. When first introduced many years ago, dual-band routers supported both 802.11a and 802.11b and were designed for business networks that used a mix of both types of Wi-Fi clients.
Some newer 802.11n Wi-Fi routers also allow simultaneous dual band communication with both 2.4 GHz and 5 GHz clients. By supplying separate network bandwidth for each of the two types of links, these routers provide maximum flexibility in setting up a home network. For example, older 802.11b/g clients can be set to run on the 2.4 GHz side of a simultaneous dual-band router without impacting the performance of 802.11n clients running at 5 GHz.

---

### Post by blackdalek on 2012-08-18
> **lindsay7 said:**
> Is this a dual band router?

I am not sure. It does have two antennae. Does that mean it is dual band?

---

### Post by lindsay7 on 2012-08-18
Your manual or the device or you can look at the rourter set up to see if it broadcasts at 2.4 and 5 ghz.

---

### Post by meamusta on 2013-01-06
Have you or someone else found a solution for this? I'm now having the same issue.

I have two laptops here but the issue is only in the old LG LW20 laptop. Both laptops run Ubuntu 12.04. Wireless network works well on my new Lenovo T400 laptop and it sees only "MyWlan", but the old one sees "MyWlan" and "MyWlan 1".

In the old laptop I can sometimes get the wireless net working for one page load by reconnecting to one of the networks, but when I try to do the next page load the browser can not find the server or the connection is timed out. After another reconnect it may be able to load the next page.

The old laptop has been connected to many different kind of networks through wire and wireless. Could there be some kind of misconfiguration left from the old connections? I haven't touched the configurations of my wireless router for ages and the wireless has been previously working also on the old laptop. I really suspect that something is wrong in the old laptop.

---

### Post by Hadaka on 2013-01-06
Hi,, click wireless icon -> Edit connections -> Wireless

highlight "Your_ESSID.1" and delete it.

have you plugged in a usb wifi?..reset mac address to your wifi card?
if so.when you create a new connection to your exsisting ESSID a new
essid.1 is created.

just noticed this is an ancient thread...sorry

---

### Post by meamusta on 2013-01-06
Thanks. It's working now.

I deleted the second network from the network manager and restarted the computer. It didn't start working right away before deleting the network so I tried the good old windows trick and it worked :)

And it is not that old thread. Only a few months ;)

---

