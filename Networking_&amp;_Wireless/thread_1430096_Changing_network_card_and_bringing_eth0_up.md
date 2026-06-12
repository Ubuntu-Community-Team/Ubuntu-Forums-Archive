---
title: "Changing network card and bringing eth0 up"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by CONCORAN on 2010-03-14
Hello,
I run an Ubuntu Server in a Virtualbox environment. Setup works fine. In virtualbox, I accidentally hit a button that generates and assigns a new mac address for the network adapter. Since then the machine does not bring eth0 up. I tried the following
ifconfig eth0 down; ifconfig eth0 hw ether macaddress; ifconfig eth0 up. Then restarted networking. But none of it seems to help.

Can someone please help bringing it up?

Thanks in advance.

---

### Post by suseendran.rengabashyam on 2010-03-15
Hi,

Try the following steps in your Ubuntu Server

1) Open the file /etc/udev/rules.d/70-persistent-net.rules using the following command
```
sudo vim /etc/udev/rules.d/70-persistent-net.rules
```

2) Delete all the lines starting with

```
# PCI device .....
```
```
SUBSYSTEM=="net", ...
```

Save and close the file.

3) Reboot your Ubuntu Server and check whether eth0 has come up properly.

Hope this helps.

---

### Post by CONCORAN on 2010-03-15
> **suseendran.rengabashyam said:**
> Hi,

Try the following steps in your Ubuntu ServerWow!!. Thanks Suseendran. It worked like charm.

---

