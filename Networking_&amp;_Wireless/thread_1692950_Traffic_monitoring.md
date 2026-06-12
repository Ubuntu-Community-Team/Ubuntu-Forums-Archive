---
title: "Traffic monitoring"
date: 2011-02-22
forum: Networking &amp; Wireless
---

### Post by delta_one_ on 2011-02-22
I am looking for a solution to monitor the amount of internet traffic used by each IP (or MAC address) on my network, so that we can tell how much data each computer is using. Does anyone know of a good program to do this? I am using Ubuntu on a computer for my router, with one interface connected to the Internet, and one interface connected to the LAN. Any suggestions?

---

### Post by aeiah on 2011-02-22
i use vnstat, but i suspect there are loads - some with a nice web gui or something. 

vnstat is a terminal app and can give you summaries of daily, weekly, monthly, last 7 day etc for up, down and total. it works on a per device basis (so you should be able to set it up for eth0 and eth1)

---

### Post by aeiah on 2011-02-22
pic

---

### Post by delta_one_ on 2011-02-22
Thanks for your reply. vnstat looks pretty good, I have just been trying it out. I am looking for a program to run on my router computer which will tell me how much data each of the other computers on the network are using, can vnstat do that? I couldn't find that option.

I am trying to get this working so that if the someone uses all of the data included in our internet plan, we can tell who it is.

---

### Post by aeiah on 2011-02-22
ahh i see. no, i dont think it will. it only monitors on a per-interface basis. the only way it'd work like you propose is if you set up a virtual interface for each computer on the LAN, which wouldn't be very practical.

maybe something more like this?:
[http://bandwidthd.sourceforge.net/](http://bandwidthd.sourceforge.net/)

or any others listed on this page: 
[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)

also you could consider webmin, with the bandwidth monitoring module.

---

### Post by delta_one_ on 2011-02-22
bandwidthd looks perfect for what I am trying to do. It installed and running.

Yes, setting up multiple virtual interfaces would have been a bit of a hassle, but it would have been possible in this case as the LAN is quite small. But bandwidthd looks like a much better solution.

I didn't know webmin had a bandwidth monitoring module, I will have to have a look at that too.

Thanks for your help!

---

