---
title: "Ditched Network Managers!"
date: 2009-03-19
forum: Networking &amp; Wireless
---

### Post by braufrau on 2009-03-19
After having silly network manager go into repeated paroxysms of requesting WEP keys I switched to WICD which, once is lost contact with the router, would hang saying "obtaining IP address". Investigations showed the problem was to do with DHCP but not how to fix it.

Just about to give up on ubuntu, I made a script based on the isntructions on this site for manually connecting to wireless. Put a launcher on the application bar with a nice icon and when the wireless goes down, maybe 1x or 2x / day,  I click that and up it comes again. 

Of course it will be a bit of mucking around if I want to connect to another wireless router, but that will be infrequently.  

So if anyone else is being driven mad by network manager or WICD, maybe they could consider this less elegant, but stable solution.

---

### Post by ugm6hr on 2009-03-19
I did the same with my Ra wifi card and serialmonkey driver.

Interestingly enough, Wicd still accurately reports the signal strength, but does the exact same hanging procedure when trying to reconnect.

Manually turning the network card down (ifdown) and back up (ifup) reconnects it again though.

It's OK for a desktop; not so helpful for a laptop or netbook you take places though!

---

### Post by braufrau on 2009-03-20
I agree .. not very helpful for a netbook .. which mine is, but it tends to stay put on the kitchen bench :)

However, when I take it on hols. to my parents, I plan to put an if statement like this ...

#! /bin/sh

f=`iwlist scan`
echo $f | grep "ssid1"
if [ $? -eq 0 ] 
then
   echo "ssid1 found"
   some commands to connect to ssid1
elif (echo $f | grep "ssid2") then
   echo "ssid2 found"
   commands to connect to ssid2
fi

and that will do me! Even if I did move around a bit, I'd probably keep connecting to the same, say 6, ssids over and over, so this would still be OK.

---

