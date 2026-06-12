---
title: "wicd install problem"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by iliketv01 on 2009-11-02
I'm trying to install wicd on 9.10 to try and get a wireless connection. I uninstalled the network manager but toward the end of the uninstall it says that network manager is lacking a resource and can't continue the process. It looks like it's uninstalled after that but when i try to install the wicd deb file it says there is a conflict with network manager. I can't see the network manager in the top taskbar by the sound anymore and it doesn't even show up in the software center as installed either. Can someone help me out with this?

Many thanks.

---

### Post by cybergalvez on 2009-11-02
I followed the instructions on this page:
[http://wicd.sourceforge.net/moinmoin/Wicd%20on%20Ubuntu](http://wicd.sourceforge.net/moinmoin/Wicd%20on%20Ubuntu)
give them a try and see if that helps

---

### Post by iliketv01 on 2009-11-02
The other problem is i don't have an internet connection unless it's wireless and i don't have wireless because of this bug in 9.10 which i'm trying to fix. The instructions on the website seem to imply that i would need a internet connection in ubuntu to do a proper installation.

---

### Post by cybergalvez on 2009-11-02
> **iliketv01 said:**
> The other problem is i don't have an internet connection unless it's wireless and i don't have wireless because of this bug in 9.10 which i'm trying to fix. The instructions on the website seem to imply that i would need a internet connection in ubuntu to do a proper installation.

if you've recently installed 9.10 then chances are the network manager package is already on your computer, so
```
sudo apt-get install -d --reinstall network-manager network-manager-gnome 
```
will most likely just reinstall your network manager, which you are going to need because you will need some type of network so you can download wicd with 
```

sudo aptitude install wicd

```

unfortunately you are going to need some type of internet connection to get wicd working

---

### Post by iliketv01 on 2009-11-02
I have a wireless router and connection, the problem is ubuntu doesn't recognize it for some reason. I'll reinstall network manager but what good is going to do me if it can't recognize my wireless signal?

---

