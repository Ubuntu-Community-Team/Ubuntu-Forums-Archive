---
title: "ubuntu 10.04.3 nvidia driver"
date: 2011-08-16
forum: Multimedia Software
---

### Post by senorian on 2011-08-16
Is there a simple way to download and install these drivers?
this site says his method does not always work:

[http://ubuntuguide.net/install-nvidia-graphical-driver-in-ubuntu-lucid-10-04](http://ubuntuguide.net/install-nvidia-graphical-driver-in-ubuntu-lucid-10-04)

thanks

---

### Post by pqwoerituytrueiwoq on 2011-08-16
install latest stable drive
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates;sudo apt-get update;sudo apt-get install nvidia-current
```
the undo line
```
sudo apt-get install ppa-purge;sudo ppa-purge ppa:ubuntu-x-swat/x-updates
```

---

### Post by senorian on 2011-08-17
please excuse my ignorance
is "undo" the uninstall code
or 
is it something that adds to the installation?
thanks (so i run it now?)

---

