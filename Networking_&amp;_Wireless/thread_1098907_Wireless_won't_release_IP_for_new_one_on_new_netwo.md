---
title: "Wireless won't release IP for new one on new network"
date: 2009-03-17
forum: Networking &amp; Wireless
---

### Post by xefialtis on 2009-03-17
I have a Laptop with a Complex Interface file for wireless networks. Not so bad, it works 100% - 90% of the time.
I go from Work to Home and it works
I go from Home to Work and it works
I go from Home to the Metro and it works
I go from the Metro to Home and it works
I go to my Brother's house, and it work
etc, etc...

But when I go from Work to the Metro, it won't release the IP address from Work...
At Work we are on the 10.111.X.X network
The Metro is on the 10.0.0.X network

SO when I go from Work (after "sudo ifdown wlan0") and get on the Metro (and use "sudo ifup wlan0=metro"), it tries to grab the previous 10.111 address instead of the new 10.0 address...

How do I clear the previous address without having to reboot (currently the only way *I* know to fix this issue)...???

Thanks

---

### Post by braufrau on 2009-03-17
This is a total guess, but worth a try,
I notice in my wicd log it issues a false IP before requesting a new one by doing this

ifconfig wlan0 0.0.0.0

Could you try that before connecting to the Metro network?

---

### Post by xefialtis on 2009-03-24
Ok, tried that, didn't work...
DId a little more research, found a bit of info on DHClient, can use dhclient -r, but that didn't work either.

SO, back to square one.

It seems that the network on the metro might need some tweaking, just because this only happens there...

I go from Home 192.168 to Metro 10.0 and NO JOY
I go from Work 10.107 to Metro 10.0 and NO JOY

I go from Home 192.186 to Work 10.107 and IT WORKS
I go from Work 10.107 to Home 192.168 and IT WORKS

I will email their tech department to see if they can troubleshoot.

But if any of y'all can thing of something else to try, I would like to give it a go...thanks!

---

