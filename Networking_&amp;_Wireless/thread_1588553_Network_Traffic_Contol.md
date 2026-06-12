---
title: "Network Traffic Contol"
date: 2010-10-05
forum: Networking &amp; Wireless
---

### Post by tomeofknowledge on 2010-10-05
I have a Ubuntu laptop and desktop that connect to the internet on wireless network "A" (Rogers MiFi) and a NAS through a wired/wireless network "B" (Wireless N Router). Ideally I would like to be able to automatically switch between wireless networks and route any Wan traffic through network "A" and Lan traffic through network "B" wired if available wireless if not. I am not even sure if this is possible but it would be my preferred setup. (I'm not opposed to a lot of work to set this up)

If the previous schema is not possible I would settle for using network "A" through wireless and network "B" wired, 

So my question is how do I route network traffic through a specific interface, and if possible how do I automatically switch wireless networks based on the type of traffic.

If someone has a more elegant solution I am open to suggestions, I have already tried DD-WRT's client and client bridge with no success and the MiFi does not support WDS.

Thank you for your time

---

### Post by Peter09 on 2010-10-05
Have a look at the 'Route' command. This should be able to specify different interfaces for different traffic. Wether it will completly do what yopu want I am unsure.
 
[http://linux.die.net/man/8/route](http://linux.die.net/man/8/route)

---

### Post by tomeofknowledge on 2010-10-07
Thanks peter that is what I was looking for.

---

