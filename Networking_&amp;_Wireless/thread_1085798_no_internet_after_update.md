---
title: "no internet after update"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by md389 on 2009-03-03
Hey everyone, 
  Following the update this morning, the update manager asked me to restart the comp. Following that my internet stopped working entirely. Can someone help me out as to why that happened/what I can do to fix it? Please help me out. 

Thanks

---

### Post by cariboo on 2009-03-03
A little more info would be helpful. Are you using wired or wireless? What is the output of:

```
ifconfig
```

The above command has to be run in an Applications-->Accessories-->Termianl. If you don't get an ip address showing in the output of the above command, in the same terminal type:

```
sudo dhclient eth0
```

substitute your network device for eth0

Jim

---

### Post by OLFP on 2009-03-05
Same problem here. It takes awhile after logging in to establish the connection, when it use to be instant. Sometimes it doesn't work, and I can't even click on the network manager icon to make changes. It's working now, so I cant post any errors.

I noticed there was a network manager update in the last set of updates.

---

