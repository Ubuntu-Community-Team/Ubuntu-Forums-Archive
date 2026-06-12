---
title: "Remote Desktop"
date: 2009-03-19
forum: Networking &amp; Wireless
---

### Post by icek on 2009-03-19
Hello, is there a way how to connect to remote computer which is not on my local network? I tried vinagre, but I wasn't succesfull, it says : connection fails. I think that I have to setup some Ip craps because I have no public IP. So is there EASY way to do this in ubuntu?

---

### Post by uzi09 on 2009-03-19
> **icek said:**
> Hello, is there a way how to connect to remote computer which is not on my local network? I tried vinagre, but I wasn't succesfull, it says : connection fails. I think that I have to setup some Ip craps because I have no public IP. So is there EASY way to do this in ubuntu?

Yes!

There are a number of ways, some better than others. You'll need to figure out the details on how to open any ports on your firewalls & also port forward correctly. These are two things that cause the most problems for people trying to achieve this. 

1. The most basic is ssh (command line version)
```
ssh user@remotehost.com
```
or
```
ssh user@xx.xx.xx.xx (where xx.xx.xx.xx is the ip address of a remote computer)

```

2. For GUI, you can use ssh with X forwarding (using the -x flag -- please see man pages for details), however NX is much better (see #3)

3. FreeNX
Super fast, secure way to connect to a GUI remotely. See the following links for a how-to set it up on your server:
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

