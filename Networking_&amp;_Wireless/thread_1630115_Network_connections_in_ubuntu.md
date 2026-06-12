---
title: "Network connections in ubuntu"
date: 2010-11-24
forum: Networking &amp; Wireless
---

### Post by hrishi.nitk on 2010-11-24
When I open my ubuntu Network connections, in the wired tab the list is as follows:
Auto Ethernet
Auto Ethernet
Auto eth0
Auto eth0

Is there anything abnormal in this? I am unable to get a wired connection.

---

### Post by grahammechanical on 2010-11-24
My connections are Auto eth0 and Auto eth1. You can add connections. In which case you give it any name you wish. It is just a label. Have you done this in the past? You do not have 4 ethernet ports. Or do you?

Regards.

---

### Post by pricetech on 2010-11-24
Yes it's unusual in that you should only have one entry, that being for ETH0.  If you have more than one NIC, the second one should be ETH1.

---

### Post by hrishi.nitk on 2010-11-26
I have only one ethernet port. Can anyone tell me the possible reasons for this kind of list?

---

### Post by Aerospaztic on 2010-12-21
Right click on your NetworkManager Applet icon on the top right of the screen (has up and down arrows).  If you go to edit connections, you can remove/add connections.  It will immediately tell you the last time you used a connection.  If you see "never" in the "last used" column, then obviously you don't need that connection and it is safe to remove.  

You might want to delete them all and create another connection.  If you end up getting stuck for some reason, you can select "edit" and enter your hardware MAC address in the "Wired" tab.  This can be found by a simple "ifconfig" command in the terminal.  Then go to "IPV-4 Settings" and apply "Automatic DHCP."  That should get the connection working.

Note:  You might want a wireless AND a wired connection.  Also, you can have a network connection (with network switch), and a separate wired connection.  Just depends on your configuration.

---

