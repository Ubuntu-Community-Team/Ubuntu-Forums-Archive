---
title: "Samba never works out of a fresh boot"
date: 2012-03-18
forum: Networking &amp; Wireless
---

### Post by SwordAngel on 2012-03-18
I am using Xubuntu Oneiric Ocelot 64-bit. I want to use Samba to share some directories to the Windows machines on my LAN.

For some reason, Samba never works correctly out of a fresh boot. Every time I boot into Xubuntu, the smbd and nmbd services would be started automatically:
```
joe@SARAH:~$ status smbd
smbd start/running, process 794
joe@SARAH:~$ status nmbd
nmbd start/running, process 1350

```

But I would never be able to immediately access the Samba service from the Windows machines on my network, even though the Windows machines can already correctly resolve my Xubuntu machine's netbios name (which I have set in "/etc/samba/smb.conf").

I would have to manually restart the smbd and nmbd services in order for the Windows machines to be able to use the Xubuntu machine's Samba service.

Can someone help me fix this annoyance?

---

### Post by Toz on 2012-03-24
It sounds like samba may be starting before the network is fully initialized and thus not working until a restart. There may be some interesting information in /var/log/samba/log.smbd.

I would suggest trying to delay the startup of smbd by altering the /etc/init/smbd.conf file; specifically the "start on" line. Suggested alternatives to try are:
```
start on (local-filesystems and net-device-up IFACE!=lo)
```
...to match the contents of /etc/init/nmbd.conf, or:

```
start on (local-filesystems and net-device-up IFACE=eth0)
```
...replace eth0 with the name of your actual network interface, or even:

```
start on (local-filesystems and net-device-up IFACE=eth0 and started udev-finish)
```
...so that it waits until udev completes its magic.

---

### Post by clive1000 on 2012-12-29
Just some quick feedback. The first piece of code above worked for me. Joined forum to give feedback - was wondering if these messages are monitored or the feedback should be given somewhere else. Took me a fair bit of time (my first samba install) to work out what was happening and find this post.

As it seems to be a timing issue here are some details of my system:

Xubuntu 12.10 server, standard install
Force GT ssd 60GB SATA III for system disk
Intel I3 2120T
Motherboard Intel DH67CF
8GB RAM
2 x HDD Raid 1

Hope this helps.

---

### Post by Toz on 2012-12-29
Thank you for the confirmation that the config change worked. It will be helpful for others who may be in the same situation.

---

