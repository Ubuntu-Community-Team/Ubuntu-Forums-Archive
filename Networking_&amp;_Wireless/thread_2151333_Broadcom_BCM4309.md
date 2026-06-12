---
title: "Broadcom BCM4309"
date: 2013-06-04
forum: Networking &amp; Wireless
---

### Post by effediti on 2013-06-04
Hi everybody,
sorry for my bad english, I've got an old Dell Latitude 610, Ram 512, I installed Xubuntu and now it works good but I've got a problem: I can't go on internet by wireless because my pc doesn't find wirless signals.

The wirless card is a Broadcom Corporation BCM4309 802.11abg Wireless Network Controller (rev03).

Does anybody help me ?

Thanks everybody


[COLOR=#101010][FONT=Ubuntu]


[/FONT][/COLOR]

---

### Post by NikTh on 2013-06-04
This probably already solved in here, but lets see some more info. 

Please open a terminal (CTRL+ALT+T) and issue the following commands one by one. (_Active Internet connection required_)


```
wget "http://ubuntuone.com/1kKCgeRTZHszxUdsSEekYz" -O ~/wirelessinfo
chmod +x wirelessinfo
sudo ./wirelessinfo
```The last command will produce a file **netinfo.txt** inside your /home folder.
Click on **"Reply to thread"** and attach the file. [See here on how to attach a file]("http://i.imgur.com/wR7EMPd.png") 


_Above is a script for debugging proposes. All the sensitive-personal data are hidden for security reasons._

---

