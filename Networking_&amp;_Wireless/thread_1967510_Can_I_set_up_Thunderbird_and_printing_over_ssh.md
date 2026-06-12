---
title: "Can I set up Thunderbird and printing over ssh?"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by foxy123 on 2012-04-28
I've got a remote laptop with a ssh access. I need to set up remotely a new user. Adding a new user account is easy with adduser but I wonder is it is possible to set up other things like Thunderbird, printers etc using the ssh access.

---

### Post by chili555 on 2012-04-28
I expect that you can. ```
ssh -l user -X 192.168.wherever
```Be sure to use -X so that you can pass back graphical interfaces. In my experience, it's a bit slow, but it works. When you are into the remote system, simply do:```
thunderbird
```...or:```
sudo system-config-printer
```

---

### Post by foxy123 on 2012-04-28
> **chili555 said:**
> I expect that you can. ```
ssh -l user -X 192.168.wherever
```Be sure to use -X so that you can pass back graphical interfaces. In my experience, it's a bit slow, but it works. When you are into the remote system, simply do:```
thunderbird
```...or:```
sudo system-config-printer
```

Cheers a lot!

---

