---
title: "Ubuntu 12.04 connects to wifi network, can't access internet"
date: 2013-05-03
forum: Networking &amp; Wireless
---

### Post by cowfish13 on 2013-05-03
Hi everyone,

I'm rather new to Ubuntu and I am have a few problems accessing the internet through Ubuntu 12.04 installed on my desktop.

I've managed to install the drivers for the USB wifi (Netgear WNDA3100v2, entirely through the help of a few Ubuntu forum posts), and it has successfully connected to my wifi network. However, I can't for the life of me get it to access any webpages which I need to install a few applications. I am currently accessing this forum page via a laptop (with Windows 7) connected to the same wifi network, so I am fairly certain it is not a general internet access issue

Curiously, when I try to load a webpage, it doesn't immediately say "Firefox can't find the server at start.ubuntu.com", it hangs for a while (around 20 seconds) on the loading stage, and then displays the error message

I was hoping someone could help me?

Thank you,
Will

---

### Post by fr2632 on 2013-05-03
This sounds like DNS issue:
[http://www.thelinuxguy.nl/how-tos/how-to-add-a-dns-name-server-in-linux-via-terminal/](http://www.thelinuxguy.nl/how-tos/how-to-add-a-dns-name-server-in-linux-via-terminal/)

---

### Post by cowfish13 on 2013-05-03
Thanks for the reply!

I tried both methods on that site. I wasn't quite sure how to find my ISP's DNS though, and when I went into:
```

nano /etc/resolv.conf
```

It said any changes I made would be overwritten. 

Would you be able to advise?

Thank you

---

### Post by fr2632 on 2013-05-07
> **cowfish13 said:**
> Thanks for the reply!

I tried both methods on that site. I wasn't quite sure how to find my ISP's DNS though, and when I went into:
```

nano /etc/resolv.conf
```

It said any changes I made would be overwritten. 

Would you be able to advise?

Thank you


Sorry for the late reply. Yes, go ahead, don't worry about that message.

If you wanna be safe, make a copy of that file:

```
sudo cp /etc/resolv.conf /etc/resolv.conf.COPY
```

and in case, to restore it:

```
sudo rm /etc/resolv.conf
sudo mv /etc/resolv.conf.COPY /etc/resolv.conf
```

Remember to restart the network after changes:

```
sudo service networking restart
```

---

