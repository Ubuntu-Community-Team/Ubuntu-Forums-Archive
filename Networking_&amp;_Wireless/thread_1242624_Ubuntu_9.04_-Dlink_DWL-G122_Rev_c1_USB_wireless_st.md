---
title: "Ubuntu 9.04 -Dlink DWL-G122 Rev c1 USB wireless stick"
date: 2009-08-17
forum: Networking &amp; Wireless
---

### Post by ninja123 on 2009-08-17
Hi all,

I have this ubuntu 9.04 minimal running. I have plugged in the DLink WLAN stick specified in the title.

I do an ifconfig and already see wlan0 with the MAC of the stick.

Initially I get an IP from the DHCP server(Dlink router)

I have test tools like hping3 and I do simple flood attack for a few seconds. Then when I restart the networking, wlan0 cannot establish link with the router.

My problem is I do manually the following configurations:


iwconfig wlan0 essid my_wlan
iwconfig wlan0 channel 7
iwconfig wlan0 key off
ifconfig wlan0 up

dhclient wlan0


And here is the trouble. The link LED glows but the stick can never communicate to the DLINK outer. It doesnt get IP address.

The 'dmesg' tells me that link is not ready.


I want to understand how the link can be again established. I 

Can you please help me out??

Is this a driver problem?

---

