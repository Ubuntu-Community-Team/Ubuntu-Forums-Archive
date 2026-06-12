---
title: "Wireless not working"
date: 2011-03-17
forum: Networking &amp; Wireless
---

### Post by conn0r on 2011-03-17
Using Wubi I installed Ubuntu with Windows 7. As soon as the startup and loading was finished i found I couldn't connect to my wireless network, it said wireless network disabled. I noticed that my Acer Aspire 5532(not sure what wifi card it has) has a Wifi button that when turned on glows orange, but stays blank when not on. It turns on automatically when Windows 7 is booting up but I can't even manually turn it on when in Ubuntu. I have no idea was wrong but looked at some other threads and couldn't figure out what to do and what was wrong.
[SIZE="4"][COLOR="Red"]PLEASE HELP!!!!!![/COLOR][/SIZE]

---

### Post by varunendra on 2011-03-19
Try this: [http://ubuntuforums.org/showthread.php?t=1336426](http://ubuntuforums.org/showthread.php?t=1336426) (pay special attention to post #10 by coffeecat)

You may have to make slight changes depending upon your OS and kernel version. Try it yourself first.

If you find it difficult or it doesn't work for you, then you may have to go through several "try & post back" type steps here. A starting point would be to open the terminal (**ctrl+alt+T**, or **Applications > Accessories > Terminal**), and post here the results of following commands:
```
uname -a
``````
sudo lshw -C network
``````
ifconfig -a
```

---

