---
title: "will this work"
date: 2010-01-19
forum: Networking &amp; Wireless
---

### Post by hyburn on 2010-01-19
hey folks,

I found a site that says it can help increase internet speed. can some1 take a look and tell me if its malicious changes or if its legit. 

[http://ubuntumanual.org/posts/10/how-to-increase-internet-speed-in-ubuntu](http://ubuntumanual.org/posts/10/how-to-increase-internet-speed-in-ubuntu)

thanks

---

### Post by chili555 on 2010-01-19
There is nothing there that looks in the least bit malicious to me. I do, however, always recommend that you keep a copy of your untouched file so you can easily and quickly restore it. In a terminal, make a backup copy:```
sudo cp /etc/sysctl.conf /etc/sysctl.conf.bak 
```Then make the suggested changes and test. If you are satisfied with the result, no further action is required. If not, then write the backup over the unneeded changes:```
sudo cp /etc/sysctl.conf.bak /etc/sysctl.conf
```

---

### Post by steveneddy on 2010-01-19
Or simply comment out your changes and save the file.

You may not gain a lot of speed, but these changes do help.

---

