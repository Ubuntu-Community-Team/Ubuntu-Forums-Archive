---
title: "need help setting up wireless connection to internet"
date: 2010-10-07
forum: Networking &amp; Wireless
---

### Post by Blue-Fox on 2010-10-07
I could use some help. I just installed Ubuntu 10.04 . Need to get my wireless router working on my HP laptop. Have been using a Linksys WRT54G Router with windows and it is working properly. Tried setting up in NetworkManager but it does not work. 

When looking at things in the Ubuntu terminal it says the network is DISABLED. 
Any suggestions will be greatly appreciated.

---

### Post by dineshs on 2010-10-08
pl post the results of (applications-accessories-terminal)
```
sudo lshw -C network
```and```
iwconfig
```

---

### Post by Blue-Fox on 2010-10-10
Thank you for your help

The issue has been resolved.  After searching for days i finally came across help from how to geek see link below.  

Every thing I needed was already in Ubuntu 10.04 
It took less than 5 minutes after installing ndisgtk

hope this saves someone some time.

[http://www.howtogeek.com/howto/17495/how-to-add-proprietary-drivers-to-ubuntu-10.04/](http://www.howtogeek.com/howto/17495/how-to-add-proprietary-drivers-to-ubuntu-10.04/)

---

