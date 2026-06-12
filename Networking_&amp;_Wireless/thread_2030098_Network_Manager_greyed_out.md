---
title: "Network Manager greyed out"
date: 2012-07-20
forum: Networking &amp; Wireless
---

### Post by sid5291 on 2012-07-20
After updating my network manager.. my edit connections is greyed all my saved settings have vanished after going through google i check my /etc/NetworkManager/NetworkManager.conf:

```
sid5291@sid:/etc/NetworkManager$ cat NetworkManager.conf
[main]
plugins=keyfile,ifupdown
dns=dnsmasq

[ifupdown]
managed=true

```

then i checked the system-connections folder:
```

sid5291@sid:/etc/NetworkManager$ ls system-connections/
adhoc
adhoc 1
adhoc 10
adhoc 11
adhoc 12
adhoc 13
adhoc 2
adhoc 3
adhoc 4
adhoc 5
adhoc 6
adhoc 7
adhoc 8
adhoc 9
Auto MyHomeNetwork
Auto MyHomeNetwork-7f442603-ec82-4dd1-a01f-0fbcfa314db6
Auto NanisNetwork
Auto NanisNetwork-0dc43517-e782-4479-bcbc-f96d72992973
Auto NanisNetwork-8114e74d-1c40-41ef-9899-7bd9b08e5f7c
Auto NanisNetwork-ac0d0ac6-3979-49a6-91bd-0eceeacbec16
Auto NETGEAR
Auto NETGEAR-51118056-e306-4b33-bd9b-98cea1e4b81f
Hotspot
MyHomeNetwork
MyHomeNetwork 1
MyHomeNetwork 2
MyHomeNetwork 3
MyHomeNetwork 4
MyHomeNetwork 5
MyHomeNetwork 6
MyHomeNetwork 7
NanisNetwork
NanisNetwork 1
NanisNetwork 2
NETGEAR
Tata Docomo Internet
Tata Docomo Internet 1
Tata Docomo Internet 1-91093403-da0b-4203-ab3c-0c327f40cc6d
Tata Docomo Internet-b676b0fc-3d6d-4fd2-9604-78323d6aade4
Wired connection 1
Wireless connection 1
Wireless connection 1-85572713-1906-41b8-92f3-fb916f140da3

```

This is what struck me as odd .. Those are the names of the wireless connections i connect to at home or at work, and the "adhoc" network is a network which i created many times maybe as many times as it has been repeated here.It seems to be creating duplicate profiles for a connection every time i connect to it. 

I am using WICD right now and it seems to work fine but i would really like to figure out what is wrong with my Network Manager

Im running Ubuntu 12.04 32-bit and i think my Network Manager is 0.9.4.1

Also im very new to ubuntu so consider me a n00b .. 

Any help would be appreciated

Thank you ! :)

here is the image showing the edit connections window
 
[IMG]https://docs.google.com/open?id=0BzbHi13Yi-02RWdmU0hoMEE5VEU[/IMG]

And this is the error i get when i try to add a wireless or wired connection 

[IMG]https://docs.google.com/open?id=0BzbHi13Yi-02UkxRV2NpNlZQT00[/IMG]

Sorry for the long post but i just wanted to make sure i cover all my bases ..
Just let me know if there is anyother information that i can provide

---

### Post by sid5291 on 2012-07-21
Just to Update i am having the exact same problem as darkcape in this thread  >>> [http://ubuntuforums.org/showthread.php?t=2028072](http://ubuntuforums.org/showthread.php?t=2028072)

---

