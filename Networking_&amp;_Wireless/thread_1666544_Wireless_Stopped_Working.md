---
title: "Wireless Stopped Working"
date: 2011-01-13
forum: Networking &amp; Wireless
---

### Post by dvlong on 2011-01-13
I'm using a Compaq V3000 laptop with a Intel Corporation PRO/Wireless 3945ABG modem. Since upgrading to 10.10 the blue indicator light and wireless switch have acted strange. I didn't worry about it until yesterday, when my wireless simply stopped working. The switch seemed to have no effect and the light stayed on orange. 

I've looked at several forums, and tried many things and nothing seemed to work. Then I found this and it brought my wireless back.

In terminal, I typed: 'sudo iwlist wlan0 scan'
and terminal returned: 'wlan0     Interface doesn't support scanning : Network is down'

Then I typed: 'sudo ifconfig wlan0 up'
and terminal returned: 'Operation not possible due to RF-kill'

Then I typed: 'rfkill unblock all' 
and I tried this again: 'sudo ifconfig wlan0 up'

and the wireless is back! 

Hope this helps someone. :)

---

