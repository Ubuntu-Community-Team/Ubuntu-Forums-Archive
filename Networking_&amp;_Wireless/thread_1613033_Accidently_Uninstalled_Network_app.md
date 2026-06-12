---
title: "Accidently Uninstalled Network app"
date: 2010-11-03
forum: Networking &amp; Wireless
---

### Post by derek826 on 2010-11-03
So my internet stopped working yesterday so in an attempt to fix it i somehow removed the network managing app.  So now i have no internet on ubuntu. I need to figure out a way to get the network app onto ubuntu again so i can have internet. Oh i have ubuntu 10.10.  

-Thanks

---

### Post by sikander3786 on 2010-11-04
What if you try

```
sudo apt-get install network-manager
```

It might install without an internet connection(??) If it doesn't download the package on some other system and install it by just double clicking. Dependecies shouldn't be a problem so download only the network-manager package here.

[http://packages.ubuntu.com/search?keywords=network-manager&searchon=names&suite=maverick&section=all](http://packages.ubuntu.com/search?keywords=network-manager&searchon=names&suite=maverick&section=all)

---

### Post by linux18 on 2010-11-04
connect to an ethernet cable and 
```
sudo dhclient eth0
```
now sudo your connected to the internet and can reinstall that package

---

### Post by garvinrick4 on 2010-11-04
Do you mean the applet up in right hand corner? in terminal:
```
nm-applet
```If whole package was tossed use post 2 or 3. This is only for the applet on upper toolbar

---

