---
title: "Ubuntu 12.04 Internet Connection Drops/Hangs? Possible solution"
date: 2012-08-03
forum: Networking &amp; Wireless
---

### Post by ChemMeister on 2012-08-03
The upgrade from 11.10 to 12.04 would have been a smooth one, if I didn't have to deal with an internet connection randomly dropping problem: 

The drop in the connection can be anything from 15 seconds to about 3  mins, and then the connection comes back. This behaviour happens while I  am actively browsing the Internet, or if I wake up the computer and  open Firefox (sometimes I have connection and sometimes I don't) . The connection when it is on is not slow (as speedtest.net results) but just "hangs" randomly like an Enzo Ferrari in Manhattan :)

 In the beginning, I thought it was a problem with the driver r8169  for my RTL8111/8168B Ethernet card on my Alienware Aurora R3, so I downloaded the r8168 from  Realtek website, followed the detailed instructions (blacklisted r8169,  changed the file to .bsh ...), but still the same problem persisted.
  So I switched to a wireless connection, and I got the same problem with Internet connection dropping randomly. 

I also saw the same problem with my Toshiba Portege.


Anyway finally I stumbled across the following command:


```
**[SIZE=3]sudo echo nameserver 8.8.8.8 > /etc/resolv.conf[/SIZE]**
```


and voilà! all problems were solved! I am not entirely sure what the above command but I just wanted to share it. 



Cheers!

---

