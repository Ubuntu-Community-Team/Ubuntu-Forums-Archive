---
title: "Open SSH to Internet"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by spiky001 on 2010-12-28
Hi I have set up ssh on a local lan all works well, GUFW takes care of the firewall of desktop with internet(No Router involved).    I wold like to open SSH to the internet, if I disable the firewall all works I can ssh user@external ip, The only problem is I,m not on a static ip, Is it possible to make a rule in GUFW that will allow me acsess from the internet? or is there a way to open ssh to the internet

---

### Post by Waappu on 2010-12-28
Hi,

You can have dynamic DNS
[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

Then you ssh e.g.
```

user@your_dyn_dns.net

```

---

### Post by spiky001 on 2010-12-28
Ok I will look into that, Dose Dynamic dns slow up internet connections? Is all traffic diverted through it I,E out going Internet etc?   In the mean time I have managed to make a rule in UFW to allow ssh connection Although I do have to know my external ip. Not ideal. I dont think it will be a permanent necessity to have outside access, so I can disable it quite easily

---

### Post by Waappu on 2010-12-28
Hi,

I'm not expert on network things.
You use dynamic DNS when you have dynamic IP. That way you have address where connect, even your machine IP changes.
DNS is for connecting to your box from internet.

---

### Post by kevdog on 2010-12-28
Using a dynamic DNS server (I use noip.com however that's is just my preference) does not slow down anything at all.  DNS records are propogated throughout the internet to many DNS servers.  

Once you get the configuration set up, I would suggest you actually spend some time reading to attempt to lock down your ssh server and restrict unwanted access.  The means of doing this are easy but there is no one best means to do this (area of great controversy).  Do some reading and ask questions here once things are set up and you've done some research.

---

### Post by spiky001 on 2010-12-28
Thks Kevdog having ssh open to internet is not something I want but I need access to it tomorrow so that I hope will be the only time,

---

### Post by kevdog on 2010-12-28
Well -- at a minimum I would suggest running it on a different port than 22, and using rsa keys rather than a password.  If you know the IP you will be connecting from you can restrict just to that IP as well, however in many cases this might not be known.

---

### Post by spiky001 on 2010-12-28
Thks for the pointers I have changed the port number already. Will look into rsa keys

---

