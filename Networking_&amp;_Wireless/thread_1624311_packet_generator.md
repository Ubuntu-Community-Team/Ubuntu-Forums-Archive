---
title: "packet generator"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by dpiddyTx on 2010-11-17
I'm looking for some feedback on packet generators for ubuntu. As a network engineer I do a lot of testing and recreations. I have some good ones for windows I run in vm but I'm looking for some good ones I can use without having to launch vm. I found a few that look promising in the repo's but can't find any reviews on them. Ideally I'd like to be able to edit the packet fields before I send them. I can do this manually but it's just a pain in the **** and I would love to have a gui. 

Thought I'd ask for some good recommendations before I go and start trying them out one by one.

---

### Post by pstavirs on 2010-11-23
Try Ostinato - [http://code.google.com/p/ostinato](http://code.google.com/p/ostinato)

It's cross-platform and supports most standard protocols.

Disclosure: I'm the developer of Ostinato

---

### Post by dpiddyTx on 2010-11-23
This is exactly what I was looking for. It looks nice but ubuntu complains when i try to install it saying it requires libprotobuf5 which I can't find in my repos. I'm not sure the difference between libprotobuf5 and libprotobuf6 but it definitely wants 5 and not 6 (I tried 6).

---

### Post by pstavirs on 2010-11-27
I guess you are using Ubuntu 10.10 - Ostinato binary packages are not yet available for this version. Till the time a binary package is available you can manually install libprotobuf5 from [http://packages.ubuntu.com/lucid/libprotobuf5](http://packages.ubuntu.com/lucid/libprotobuf5) and then try installing Ostinato.

Alternatively you can try to compile Ostinato from source. For instructions, see [http://code.google.com/p/ostinato/wiki/BuildingFromSource](http://code.google.com/p/ostinato/wiki/BuildingFromSource)

---

