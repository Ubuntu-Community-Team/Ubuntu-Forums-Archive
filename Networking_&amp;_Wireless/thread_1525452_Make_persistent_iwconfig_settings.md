---
title: "Make persistent iwconfig settings?"
date: 2010-07-06
forum: Networking &amp; Wireless
---

### Post by damatta on 2010-07-06
Hiya..
ubuntu is capping my wireless connection at 1Mbps, so everytime I boot up i have to type this:
"iwconfig wlan0 rts 2347 && sudo iwconfig wlan0 frag 2346 && sudo iwconfig wlan0 rate 9MB"

How can I make these settings persistent?
Cheers

---

### Post by Brandon Williams on 2010-07-07
If you chmod /etc/rc.local to make it executable, you could put those commands into /etc/rc.local (without sudo, since they'll be run as root anyway). This method will only work if running the commands _before_ associating the interface to the network functions correctly. If that doesn't work, then you could consider creating a startup application for your user session that runs the commands for you after giving enough time for the interface to associate to the network, something like:
```
#!/bin/sh
sleep 60
sudo iwconfig ...
```

If you need more detailed explanations of either of those methods, let us know.

---

### Post by damatta on 2010-07-07
Thanks for the reply. The second method is working great.
The thing is that my wifi driver is awfully bad. Even though my wifi configuration is optimal it goes slow from time to time.
rtl8180 is for sure a very problematic driver..

---

