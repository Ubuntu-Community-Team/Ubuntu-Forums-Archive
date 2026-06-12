---
title: "How to temporarily mask/change MAC address"
date: 2012-05-10
forum: Networking &amp; Wireless
---

### Post by bananaboatcoat on 2012-05-10
Hello, 

How can we temporarily mask or change the computer's MAC address?

---

### Post by ammofreak on 2012-05-10
Hi ):P
See the following link: [http://share-facts.blogspot.ca/2009/02/change-mac-address-in-ubuntu.html](http://share-facts.blogspot.ca/2009/02/change-mac-address-in-ubuntu.html). Hope this helps u...:)

---

### Post by idoitprone on 2012-05-11
> **bananaboatcoat said:**
> Hello, 

How can we temporarily mask or change the computer's MAC address?
```
 sudo apt-get install macchanger
```


```
sudo macchanger -r interfaceName
```

example
```

sudo ifconfig eth0 down
sudo macchanger -r eth0
sudo ifconfig eth0 up
```

macchanger will only work if the interface is down
the mac address should be different

---

### Post by mörgæs on 2012-05-11
Moved to the network forum.

---

### Post by bananaboatcoat on 2012-05-21
> **idoitprone said:**
> ```
 sudo apt-get install macchanger
```Hi, idoitprone.
I tried that command but got:[QUOTE]
ubuntu@ubuntu:~$ sudo apt-get install macchanger
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package macchangerI'm using Ubuntu 12.04 Live (on USB)


UPDATE: found the Deb in [http://www.ubuntuupdates.org/package/core/precise/universe/base/macchanger](http://www.ubuntuupdates.org/package/core/precise/universe/base/macchanger)

---

### Post by Lars Noodén on 2012-05-21
You should also be able to go to System Settings -> Network -> Wired -> Options and set it there.

---

### Post by bananaboatcoat on 2012-05-21
Lars, I'm there now, but when I change the "Device MAC address", the "Save" button becomes unclickable.

---

### Post by Lars Noodén on 2012-05-21
Hmm.  In one dialog it shows me it has changed. Yet in another it has not.  

If you do it by hand, it is this way:

```

sudo ifconfig eth0 down
sudo ifconfig eth0 hw ether *xx:xx:xx:xx:xx:xx*
sudo ifconfig eth0 up
ifconfig eth0

```

---

