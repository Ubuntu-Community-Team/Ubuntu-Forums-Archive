---
title: "Network Connections blank, ifconfig shows NIC"
date: 2011-02-10
forum: Networking &amp; Wireless
---

### Post by jadonchristensen on 2011-02-10
Hi all,

I messed up my Network Connections when I put a different NIC in my computer. Now I just went back to using the old NIC. It shows up in ifconfig, but the GUI Network Connections is blank. When I manually Add the connection back to the GUI Network Connections, the settings are not reflected when doing ifconfig.

For example, I change the IP address for eth0 in GUI Network Connections, save the settings, do ifconfig and it is stuck using the old information.

How can I fix this?

Thanks for your time.
Ubuntu 10.10

---

### Post by amsterdamharu on 2011-02-10
Could you post the output of the following command?

```
cat /etc/networks
```

---

### Post by jadonchristensen on 2011-02-11
default		0.0.0.0
loopback	127.0.0.0
link-local	169.254.0.0
localnet	192.168.0.0

The GUI Network Connections is still blank. I went ahead and setup the networking manually (command line), but I'm still puzzled as to how to get it to show in the GUI.

---

### Post by amsterdamharu on 2011-02-11
If you'd like to use the network manager then the networks file need to be empty except the 
link-local 169.254.0.0
line

Best you remove all networks from network manager first, right click the network manager applet and choose edit connections. Remove whatever connections you got there.

You can edit the file using the following command:
```
service network-manager stop
sudo nano /etc/networks
```
Delete all the lines except the link-local one and press control + x then y and enter.
Now start network manager:

```
service network-manager start
```

Now the network manager applet should have something like Auto eth0. If you need a fixed ip you can right click and choose edit connections. Click on Auto eth0 and then edit and you'll be able to edit it.

---

### Post by jadonchristensen on 2011-04-19
I blanked out the files completely and that worked, after rebooting.

sudo gedit /etc/network/interfaces
sudo gedit /etc/networks

---

### Post by Iowan on 2011-04-19
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")? :)

---

### Post by jadonchristensen on 2011-04-19
> **Iowan said:**
> [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")? :)

Yes, solved. Thank you

---

