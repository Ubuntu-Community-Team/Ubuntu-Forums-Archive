---
title: "Wired and Wireless connections gone/not working"
date: 2012-09-13
forum: Networking &amp; Wireless
---

### Post by mazinho81 on 2012-09-13
Hiya,
 
As a literal computer illiterate I am posting a question to a problem which I have come across while reading this forum, but none of the solutions seemed to work for me.
 
I have an Asus Eee PC Seashell Series Notebook & use Ubuntu 12.04, and recently my friend was trying to configure a wired internet connection for me and after typing some commands, not only was I not able to connect though cable, but my wifi is also gone (was working fine before). Also, while booting the notebook I get a message saying Booting without Network Configuration (or something similar). I have seen posts on this forum with simlar problems, but I have not been successful myself.
 
Any help would be greatly appreciated. :p

---

### Post by OrangeMadness on 2012-09-17
If your computer is booting without Network, most likely it cannot bring up your interfaces (eth0 if you have a wire connected and wlan0 for your wireless connection)

```
cat /etc/network/interfaces
```so we can have a look at this.

Also try to bring up your interfaces down & up manually by executing:

```

ifdown -a
ifup -a

```Any error messages following the execution of these commands would be helpful finding the problem.

Also the output of:
```

lshw -class network

```would be useful - shows if the system recognizes your Ethernet and Wireless LAN controllers.

And of course paste the output of:
```

ifconfig -a

```

---

