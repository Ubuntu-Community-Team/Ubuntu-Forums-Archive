---
title: "how to disable firewall"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by adityadeva on 2009-05-22
I had installed firewall in my 8.04 Hardy 2.6.24. firestarter and guarddog. I uninstalled them both. 

after this my computer stoped connecting to internet. my dsl modem is in configured to connect to the net by just pluggin in the network cable.

I enabled ufw. and i could ping to the modem as well as connect to net. but after every reboot i had to enable ufw manually. I have a passwordless login to the desk top.

i installed gufw. but now just after  logging into the desktop gufw prompts for admin password. If cancel is pressed then computer fails to connect to the net. I am under pressure to rectify this problem as the computer is used by several people to acess the net. 

pls tell me how to bring my computer back to the state when it automatically logged into the desktop and ran without a firewall

---

### Post by binbash on 2009-05-22
sudo ufw disable

---

### Post by adityadeva on 2009-05-28
> **binbash said:**
> sudo ufw disable

whenever i disable ufw/gufw and reboot i am not able to get my internet connection. gufw asks for admin password every time we **_automatically_** log into desktop.

since many people use this machine to access internet, i wish the net got connected without user intervention


pls help

---

### Post by dmizer on 2009-05-28
Please post the output of the following:
```
sudo iptables -L
```
Do you have firestarter installed?

---

