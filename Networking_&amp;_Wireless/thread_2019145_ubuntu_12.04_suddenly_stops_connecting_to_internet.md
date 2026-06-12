---
title: "ubuntu 12.04 suddenly stops connecting to internet via wifi"
date: 2012-07-07
forum: Networking &amp; Wireless
---

### Post by vicky_ on 2012-07-07
HI, 

This happens often for my ubuntu 12.04. 

I'm using ubuntu on my laptop and connect to internet via wifi. 

Sometimes even though the connection is established with the modem I'm unable to connect to the internet. 

at that times I'm also unable to connect to 192.168.1.1, which should give me the page to my modem even if there is no internet connection to the modem. 

this is the reason for me to belive that ubuntu has a serious connectivity issue. 

Since I have dual boot on my laptop (ubuntu 12.04 + Windows 7) I start my system with windows 7 and the problem is gone and I'm able to connect to the internet. 

This hits on my productivity levels. I seriously want to work on ubuntu and I'm forced to get windows to get internet connectivity. 

I observed this whenever I start Thunderbird and Whenever there is a software update taking place using the ubuntu software updater. 

and many times while just surfing the internet. 

Any help is appreciated. Do you need any info from my side please let me know. 

Thanks and Regards, 

Vic

---

### Post by Kirk Schnable on 2012-07-11
From the screenshot you provided me, it looks like it may just be your DNS that's not working.

DNS is Domain Name Services.  It is the software which takes a name "www.google.com" and translates it to an IP address "74.125.236.82".

Since you can connect to your router, your computer has a local IP address, and its wireless connection is working correctly.

Let's have a look at your DNS settings.  Next time it stops working, in your terminal window, run this command.  Then get the output to us.

```
cat /etc/resolv.conf
```

And while we're at it, we'll make sure your default gateway is correct.

```
ifconfig
```

```
route -n
```

That information should give me a better basis to help you.

As a heavy Ubuntu user at home and work, I guarantee you that Ubuntu 12.04 does not have a "serious connectivity issue".  I'm sure this is an isolated incident, and we should be able to get it fixed for you.

Kirk

---

