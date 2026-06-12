---
title: "multiple wireless interfaces &amp; networkmanager"
date: 2009-12-24
forum: Networking &amp; Wireless
---

### Post by ulugeyik on 2009-12-24
Hello,

Sometimes I like using an external, USB wireless interface instead of the internal one on my laptop. I do this to improve my reception. For example, recently, we were renting a place and wireless router was a floor below us and we could get reception through the window only. With older versions, I did this by playing with ifup/ifdown/iwconfig, /etc/network/interfaces etc. However, with networkmanager, a lot things are happening automagical and the moment I get the external card running everything freezes. I can keep this from happening by disabling wireless first but when I enable it before I can select anything, it happens. I think two interfaces are confusing each other. 

Is there a good solution for this?

---

### Post by shredder12 on 2009-12-25
well, if you can still do it manually by editing the interfaces file and iwconfig etc.. then network manager will automatically ignore that interface after looking at ur manual config in interfaces file. so, the system won't freeze anymore..

and if you want to prevent the freezing while doing so.
you can just stop the network-manager for that while..
```
sudo /etc/init.d/network-manager stop
```
and use "start" in the above command to start it again once u r done..

---

### Post by ulugeyik on 2010-01-06
Fiddling with those manually seem to mess up network manager in general :<

---

