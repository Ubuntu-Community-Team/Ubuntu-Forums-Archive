---
title: "Wifi Internet Connection problem when connected to a network via Lan"
date: 2012-11-13
forum: Networking &amp; Wireless
---

### Post by brainhammer on 2012-11-13
My system is Ubuntu 12.04, 32 bit.

I am facing some problem with my wifi internet connection after I have connected to a network via LAN.

When I connect to the LAN, then I lost the internet connection. After disconnecting from the LAN, the wifi [internet] connection works again.

Here is the two tabs, after I connect to the LAN:

[IMG]http://img341.imageshack.us/img341/3749/selection010r.png[/IMG]

and 

[IMG]http://img13.imageshack.us/img13/8263/selection011i.png[/IMG]

This above settings fail to connect to internet.

After I disconnect from the LAN network, then the internet [wifi] works again. Here is that settings:

[IMG]http://img829.imageshack.us/img829/4003/selection012v.png[/IMG]

I want to connect to internet always, and also want to share my Wifi internet connection via the LAN. But dont have idea how to do this. 

Thanks in advance.

--------
Edit:
My wifi works with the default network settings, dont require any IP or DNS. I have set it for the LAN by editing:
```
sudo gedit /etc/resolv.conf
```

---

### Post by brainhammer on 2012-11-18
can anyone help me to find out how to connect with internet [via Wifi] while I am also connect with a office network through LAN?

---

### Post by ahallubuntu on 2012-11-18
Your wired connection is your default connection, so internet traffic will try to go through its gateway.  I don't know how to set the default connection to be wireless with 12.04 but look around in the network options, you can probably figure it out.

Also make sure the wired LAN you are connecting to is on a different subnet than the wireless LAN.  If both are say 192.168.1.something, you'll only be able to get to one network or the other but not both.

---

