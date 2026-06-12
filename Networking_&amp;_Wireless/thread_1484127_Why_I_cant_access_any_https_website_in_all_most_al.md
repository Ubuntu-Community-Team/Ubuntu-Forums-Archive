---
title: "Why I cant access any https website in all most all browsers?"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by Martian911 on 2010-05-15
Some days ago I just installed BZflag,a kind of tank game which require to add some ssl deb packages.I think since then I cant access any https website.I tried firefox\Netscape\Opera\Chrome\Arora even Medori,but no one is normal.I tried ssh access and it works well.The problem is just that browsers cant access the ssl based site.For example,if I go to the login page of hotmail,it just shows "Login" as the title of the tab but shows a blank page.Or When I want to login to twitter,firefox showed the error code ssl_error_rx_record_too_long.Anyone know what's wrong?I'd already uninstalled the BZflag with all the packages use by itself.
Thanks for all your time.

---

### Post by bovcan on 2010-05-15
Did you open SSL port (443)?

---

### Post by Martian911 on 2010-05-15
I can use ssl when I just installed kubuntu 9.10 ,but since some days ago it doesn't work.So I think it might not caused by 443 port.
I just use the command netstat -an | grep 443 to check for it and it said ssl connection has already established.

---

