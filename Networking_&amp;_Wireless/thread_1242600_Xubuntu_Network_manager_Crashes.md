---
title: "Xubuntu Network manager Crashes"
date: 2009-08-17
forum: Networking &amp; Wireless
---

### Post by Neill_R on 2009-08-17
Hi

Who would have mobile Broadband.It is stable for hours and then acts like a Mexican dog stuck in treacle. This is the second time I have entered this post.Hopefully i will not have problems this time.

The problem
------------------
I have seen my network go down and reconnect, however, I believe (not proved) that sometimes it goes down and then does not reconnect. When this happens the network manager icon (a radio tower in my case (mobile broadband) turns to a disconnected network icon symbol and says the network manager is not running. If I reboot all is returned to normal ans connection is resumed.


As you can see below my laptop is acting as a firewall gateway with internet connection sharing to my router.

Orange ~~~~~~ ICON225(USB) ------HP Laptop (Xubuntu 9.04) eth0-----Router --- PCS


_***How can I restart the network manager with out rebooting.***_

Many thanks in advance

---

### Post by GeorgeVita on 2009-08-18
> **Neill_R said:**
> ...
_***How can I restart the network manager with out rebooting.***_

Hi **Neill_R**, you can try:```
sudo /etc/init.d/NetworkManager --help
```your options are: **start stop restart force-reload status**

try first **status** to see if it is stoped and then:```
sudo /etc/init.d/NetworkManager restart
```
Regards,
George

---

### Post by Neill_R on 2009-09-01
George 

Next time it happens I will try 

sudo /etc/init.d/NetworkManager force-reload

---

