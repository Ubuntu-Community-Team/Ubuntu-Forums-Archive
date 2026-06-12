---
title: "Problem mit WLAN after Upgrade to 9.10 - unknown error 132&quot; wlan0"
date: 2010-01-03
forum: Networking &amp; Wireless
---

### Post by Skeeve245 on 2010-01-03
Hi everybody,

I promised I searched for a solution almost the whole day, partly in the internet partly in this forum - but found no solution.

After I upgraded to the latest KUbuntu using aptitude like 2 month ago, I lost my WLAN connectivity.

On root@Aahz:~# ifconfig wlan0 up I get "unknown error 132" wlan0.

In some article I found a manual solution: root@Aahz:~# rfkill unblock all and root@Aahz:~# ifup wlan0.

But after a while I think that solution sucks.

I would like to use the KNetworkManager again for automatic connection to my network instead of always having to start the shell to fumble around.

Anybody an idea? Any help is greatly appreciated.

Thanks


Stefan

---

### Post by Skeeve245 on 2010-01-03
Please DO NOT answer in this thread / Unfortunatelly I created two, please use the other one - Sorry for the confusion!!!

---

