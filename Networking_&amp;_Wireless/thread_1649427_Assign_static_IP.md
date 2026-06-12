---
title: "Assign static IP"
date: 2010-12-20
forum: Networking &amp; Wireless
---

### Post by gpdas on 2010-12-20
Hi, I am new to Ubuntu Server. I would like to assign a static IP to my server. Pl help in configuring from command line. Thanks.

---

### Post by matt_symes on 2010-12-20
Hi  

You need to edit your

```
/etc/network/interfaces
```

file to add a static ip address.

Have a look at 

```
man interfaces
```

Kind regards

---

### Post by puppywhacker on 2010-12-20
You can also right-click the arrow-up/down-icon and edit the network device.

---

