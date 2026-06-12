---
title: "Where is wvdial.conf in ubuntu 9.04 beta"
date: 2009-04-16
forum: Networking &amp; Wireless
---

### Post by mahenkpatel on 2009-04-16
I just installed ubuntu 9.04 beta in my laptop, but i cannot find the wvdial component in it which i used to connect my Datacard in earlier versions. I tried installing it from a .deb file i downloaded but it says that i dont have permission to do the job.

what should i do, is wvdial not inbuilt in ubintu 9.04 beta???

---

### Post by chili555 on 2009-04-16
It you have any alternate means to access the internet, you can:```
sudo apt-get install wvdial
```If not, you can get it here and transfer it on a USB stick, CD, etc.: [http://packages.ubuntu.com/jaunty/wvdial](http://packages.ubuntu.com/jaunty/wvdial) It may also be on the install CD:```
sudo apt-cdrom add
sudo apt-get install wvdial
```

When you are warned that you don't have permission to install a package, use 'sudo':```
sudo dpkg -i yourlilpackage.deb
```

---

