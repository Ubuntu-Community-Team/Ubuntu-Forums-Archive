---
title: "intel 4965 and wifi to ethernet bridging"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by thebinaryblob on 2010-08-10
I have been trying to get my laptop to share its wireless connection to my older, wireless-less, computers through its ethernet port. So far, I have not been able to make it work. As far as I know, what I am trying to do is called network bridging. The method I have been trying so far is to run these commands as root:
```
ifconfig wlan0 -promisc
brctl addbr br0
brctl addif br0 wlan0
brctl addif br0 eth0
ifconfig br0 up
```Each time I do this, the system running as a bridge loses connection, and the system being bridged to never gets a connection. My hardware is:
```
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

```

---

### Post by mprokolo on 2010-08-11
have a look at [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
for internet connection sharing 

P.S. It is possible to do it with bridging but this is a bit more easy

---

### Post by pastalavista on 2010-08-11
You might want to look at [Firestarter]("http://www.fs-security.com/docs/connection-sharing.php") for a GUI solutiion. It's in the repositories
```
sudo apt-get install firestarter
```.

---

### Post by thebinaryblob on 2010-08-11
the connection sharing option in the network manager worked. I can't believe I was trying to do this with bridging!

---

