---
title: "Stop Wireless Networking"
date: 2010-03-19
forum: Networking &amp; Wireless
---

### Post by johnathanamber on 2010-03-19
Hello everyone!

Back in the days of jaunty I had this script to automatically change my MAC address:

```

/etc/init.d/network stop
macchanger -r eth0
macchanger -r wlan0
/etc/init.d/network start

```

The above worked great. However in karmic, it does not work.

I've looked at different ways of doing this to no avail:
> 
/etc/init.d/networking stop
>> Deconfiguring networking interfaces [ OK ]

stop networking
>> stop: unknown instance

service networking stop
>> stop: unknown instance

ifdown -a
(returns nothing)

ifdown wlan0
>> ifdown: interface wlan0 not configured (But I have used this to connect to multiple wireless networks)


So I am kinda stuck.

What do I do to stop the wireless adapter so I could change its MAC address in karmic?

Thank you and God bless,
Johnathan

---

### Post by johnathanamber on 2010-03-19
OK, OK, figured it out.

Using the network manager, I wasn't sure if it actually disabled the wireless or simply allowed another application manage the wireless (like in Windows).

if you R/C on the network manager you can uncheck the wireless and the Networking boxes to disable the wireless.

After disabling them I was able to change the MAC address with no issue.

Thank you for your help and guidance.

God bless,
Johnathan

---

