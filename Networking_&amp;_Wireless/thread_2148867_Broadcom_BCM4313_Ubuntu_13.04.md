---
title: "Broadcom BCM4313 Ubuntu 13.04"
date: 2013-05-26
forum: Networking &amp; Wireless
---

### Post by StenchySocks on 2013-05-26
Okay, so after installing Ubuntu 13.04 I realized my internet connection was terrible unless I was really close to the router. So I installed the proprietary drivers from the "Additional Drivers" section and everything was working great. My internet was exceptionally fast and everything was working perfect. The problem I am having is my computer is using ALL the bandwidth of my router; on other computers in my home I can't access the internet at all when my computer is turned on. As soon as I turn the wireless off of my computer, internet on the other computers resume to the norm. How can I fix this? :confused:

---

### Post by carl4926 on 2013-05-26
> [COLOR=#000000]The problem I am having is my computer is using ALL the bandwidth of my router;[/COLOR]The wireless driver has nothing to do with this.
Bandwidth use is to do with what you are running ie; bittorrent

If you are sure nothing is supposed to be running. Open the System Monitor and look at the Network activity

---

### Post by StenchySocks on 2013-05-26
Nothing seems out of the norm with my network activity. This problem only happens after I have the drivers installed. Even on idle, when nothing is running, I can't connect to the internet on other computers.

---

### Post by Sef on 2013-05-26
What is your wireless on your computers? Are they A? B? G? N? If your computer is G, and the others are N, then the other computers would run a G speed when you have your computer's wireless on.

---

### Post by carl4926 on 2013-05-27
> **Sef said:**
> What is your wireless on your computers? Are they A? B? G? N? If your computer is G, and the others are N, then the other computers would run a G speed when you have your computer's wireless on.

True, good point
But the OP said: > [COLOR=#000000]on other computers in my home I can't access the internet at all[/COLOR]

I wonder if the OP has tried b43 driver?

---

### Post by carl4926 on 2013-05-27
And of course, are the other computers Wireless or Wired?

---

### Post by axelsvag on 2013-07-07
> **carl4926 said:**
> And of course, are the other computers Wireless or Wired?

I can not say I have the solution, but I have exactly the same problem, When I use the additional driver for wireless it uses all the network bandwith with very little to the other computers in the network.

---

### Post by trudi on 2013-07-10
I have exactely the same issue with a HP Pavilion DV7. Now I'm using my mobile as a router to let my wife surf on the wi-fi... :(

Edit : of course this does not happen in Windows (I'm in dual boot). So that doesn't seem to be related to the wifi access point.

---

### Post by trudi on 2013-08-25
I found an alternative solution on my NETGEAR WNR1000v3 router by enabling the guest wifi, with WPA2-PSK password and with "Wireless Isolation" feature enabled (the wireless client under this SSID can only access internet and it can’t access other wireless clients even under the same SSID, Ethernet clients or this device. Other clients can’t access the wireless client, either.).

Now my wife and our mobile phones can connect to the normal wifi login without being disturbed by my Ubuntu 13.04 laptop.

---

### Post by chili555 on 2013-08-25
> **trudi said:**
> I found an alternative solution on my NETGEAR WNR1000v3 router by enabling the guest wifi, with WPA2-PSK password and with "Wireless Isolation" feature enabled (the wireless client under this SSID can only access internet and it can’t access other wireless clients even under the same SSID, Ethernet clients or this device. Other clients can’t access the wireless client, either.).

Now my wife and our mobile phones can connect to the normal wifi login without being disturbed by my Ubuntu 13.04 laptop.I believe the Broadcom STA driver is incorrect for this device and I believe it *does* swamp the router. I have seen it many times. If you'd care to experiment, trudi, please open a terminal and do:```
sudo apt-get remove --purge bcmwl-kernel-source
```Reboot and give us your report.

---

