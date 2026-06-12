---
title: "Troubling getting qt dependencies"
date: 2015-01-18
forum: Multimedia Software
---

### Post by derek28 on 2015-01-18
[https://github.com/Cockatrice/Cockatrice/wiki/Installing-Cockatrice#on-linux](https://github.com/Cockatrice/Cockatrice/wiki/Installing-Cockatrice#on-linux)
I got instructions there that I've used before on this computer with kubuntu and lubuntu, I decided to go back to good ol' ubuntu for it's reliability and this is what happened. 


[http://packages.bodhilinux.com/bodhi/pool/main/c/cockatrice/](http://packages.bodhilinux.com/bodhi/pool/main/c/cockatrice/)
I got a .deb cockatrice package here that I know to be good.  



derk@derk-HP-Stream-Notebook-PC-11:~$ sudo apt-get install build-essential g++ qtmobility-dev libprotobuf-dev protobuf-compiler libqt4-dev
[sudo] password for derk: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package qtmobility-dev
derk@derk-HP-Stream-Notebook-PC-11:~$ sudo apt-get install libqtmultimediakit1   <----(this is the dependency that Ubuntu Software Center said couldn't be satisfied)
Reading package lists... Doney 
Building dependency tree       
Reading state information... Done
E: Unable to locate package libqtmultimediakit1
derk@derk-HP-Stream-Notebook-PC-11:~$ 



All the repositories are checked, idk what to do.

---

### Post by mc4man on 2015-01-18
go sudo apt-get update & then try again.

```
sudo apt-get update && \
sudo apt-get install build-essential g++ qtmobility-dev \
libprotobuf-dev protobuf-compiler libqt4-dev
```

---

### Post by derek28 on 2015-01-18
thank you very much! I knew I needed to update, just didn't think that was the problem.

---

