---
title: "firefox issue on dual system ?"
date: 2010-08-07
forum: Networking &amp; Wireless
---

### Post by FD Shaw on 2010-08-07
Just downloaded latest dual operating Desktop version of Ubuntu onto new Acer netbook-all OK except for getting firefox browser to get any web site on ubuntu- however  firefox to Web  OK on other OS (Windows 7 starter system). Linsky Cisco wireless modem connection stated as OK but does drop out sometimes on _ubuntu only_  The modem is also hardwired to a Desktop computer- no problems here -  I have not installed any additional firewall (yet) for ubuntu Thanks in anticipation of suggestions-Derek

---

### Post by lovinglinux on 2010-08-07
Disable ipv6 on Firefox Preferences, by setting the **network.dns.disableIPv6** preference to **true**.
[LIST=1]
[*]Type **about:config** in the address bar, press Enter.
[*]Find network.dns.disableIPv6 in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]

---

### Post by FD Shaw on 2010-08-10
> **FD Shaw said:**
> Just downloaded latest dual operating Desktop version of Ubuntu onto new Acer netbook-all OK except for getting firefox browser to get any web site on ubuntu- however  firefox to Web  OK on other OS (Windows 7 starter system). Linsky Cisco wireless modem connection stated as OK but does drop out sometimes on _ubuntu only_  The modem is also hardwired to a Desktop computer- no problems here -  I have not installed any additional firewall (yet) for ubuntu Thanks in anticipation of suggestions-Derek
Thanks lovinglinux for suggestion of  setting the **network.dns.disableIPv6** preference to **true**. which I did but to no avail-.  I am getting a message from Linksys that it is disconnected.( Win 7 continues to function with Linksys)

---

### Post by lovinglinux on 2010-08-10
I also have a Linksys, but it has been a while since the last time I had to configure it.

Check if you have the correct MTU in the router settings. If you have 1500 instead of 1492 then it could cause connection issues.

Also make sure you have the proper authentication key configured in the network manager.

I can't access my machine which uses the wireless right now, so I can't provide the correct steps to do that, but someone else will probably post it soon.

---

### Post by FD Shaw on 2010-08-14
> **lovinglinux said:**
> I also have a Linksys, but it has been a while since the last time I had to configure it.

Check if you have the correct MTU in the router settings. If you have 1500 instead of 1492 then it could cause connection issues.

Also make sure you have the proper authentication key configured in the network manager.

I can't access my machine which uses the wireless right now, so I can't provide the correct steps to do that, but someone else will probably post it soon.

Yes, the problem was the authentication key- just lifted/ and fitted the  same key as in Win 7 and it then worked-thanks a lot

---

