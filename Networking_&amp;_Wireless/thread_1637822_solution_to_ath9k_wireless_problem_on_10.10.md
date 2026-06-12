---
title: "solution to ath9k wireless problem on 10.10"
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by danburyct on 2010-12-05
I am writing this post in the hopes that anyone with the same problem will find this to be perhaps a solution.

I started having problem with my wireless connection on my ASUS EEE PC 1000HE after upgrading to 10.10.  Getting an IP from my router seemed to be hit or miss.  I disabled my wireless a few weeks back while on the train to conserve battery power.  I tried to turn the wireless back on after getting home, but I could not get my wireless to work.  I was able to use a wired connection.  I upgraded the wireless drivers for ath9k, but that did not solve the problem.  However, it did seem to improve the strength in the signal.  I tried hard coding the wireless information in /etc/network/interfaces but that did not work.  I tried turning on debugging with modprobe ath9k debug=0xffffffff   but that did not reveal anything.   I had a dual boot, so I check the windows boot and the wireless worked fine on there. I finally came across an  entry in daemon.log regarding the DHCP process.  Device 'wlan0' IP6 addrconf timed out or failed.  I looked over issues to try to figure out how to disable ipv6 by changing settings in /etc/sysctl.conf.  These did not work for me.  Finally I came across a post to check out the Network Connections.  

 System -> Preferences -> Network Connections and clicked on the Wireless tab.  I selected my router's ESSID and then clicked edit.  under the IPv6 tab I changed the drop down from automatic to ignore.  As soon as I did this, my connection came back up. 

  Best Regards

           Ty

---

### Post by vigyani on 2011-03-26
Hi

As suggested on my system IPv6 is set to "ignore" but I still have the simillar problem. Most of the time my system soes not connect to AP, somethimes it does randomly. 
I do not know what it causing problem?

Any help would be appriciated.

Thanks

---

