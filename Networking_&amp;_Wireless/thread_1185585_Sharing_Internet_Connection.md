---
title: "Sharing Internet Connection"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by Jcdlvsrbld on 2009-06-12
ubuntu 9.04 32-bit
I was wondering how i can share my laptop's internet connection via the open ethernet port (basically using the laptop as an extension wireless reciever for another device). i know how it is done on mac and windows laptops, but i can't seem to figure it out for ubuntu. Any help??

---

### Post by romizone on 2009-06-12
> **Jcdlvsrbld said:**
> ubuntu 9.04 32-bit
I was wondering how i can share my laptop's internet connection via the open ethernet port (basically using the laptop as an extension wireless reciever for another device). i know how it is done on mac and windows laptops, but i can't seem to figure it out for ubuntu. Any help??

Install SQuid in Your laptop , and make your laptop become Proxy to another PC inside your network .

It is a simple way to share your internet connection ^_^:popcorn:

---

### Post by Jcdlvsrbld on 2009-06-12
the problem is
i'm not trying to connect to another computer.
and im trying to share the connection over a cat5

---

### Post by kzersatz on 2009-06-12
By turning your PC into a proxy you are going to allow the connection to be shared

In windows its called bridging a network connection, Linux I'm not sure what its called but according to the description of romizone's post Squid should allow you to do this

---

### Post by Jcdlvsrbld on 2009-06-12
will firestarter have the same effect?

---

### Post by jimv on 2009-06-12
Yes, firestarter will work just fine.  The only caveat is that you need to also install the dhcp3-server package.

---

### Post by Iowan on 2009-06-12
You've probably already seen [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") one - maybe even the [wireless]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") link near the bottom... but just in case.

---

