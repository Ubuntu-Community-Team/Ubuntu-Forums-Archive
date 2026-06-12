---
title: "Deluge &quot;No incoming connections&quot; NetComm router help"
date: 2009-04-16
forum: Networking &amp; Wireless
---

### Post by Nuticulus on 2009-04-16
Hi,

I'm using Deluge to download torrents, and manage to get ok speeds on heavily seeded torrents, but it says that there are no incoming connections. I'm using a NB5Plus4 ADSL2+ modem router. Can anyone help me configure my router correctly?

---

### Post by MaindotC on 2009-04-16
The only configuration you should need is forwarding ports.  Open your torrent client and check the preferences - it should say what ports it is using to download - usually in the 10,000 range.  I used bittorrent before it used 10,000-10,010.  Log into your router and forward the ports to the ip address of the machine that is doing the downloading.

---

### Post by Nuticulus on 2009-04-16
I set the router up to forward the port Deluge's active port is set to, following the instructions on [http://portforward.com/english/routers/port_forwarding/Netcomm/NB5Plus4/Echolink.htm]("http://portforward.com/english/routers/port_forwarding/Netcomm/NB5Plus4/Echolink.htm"). But Deluge is still downloading at ~5 Kib/s and saying "No incoming connections". Is there some way I can test if port forwarding has been successfully set up?

---

### Post by superprash2003 on 2009-04-16
do you have firestarter or anything similar running? you could use this online port scanner to see if port is successfully open.. run this scanner only when deluge is running [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---

### Post by Nuticulus on 2009-04-16
I checked the port, which is apparently closed. And no, I don't have firestarter. I'll have another look at the router settings...

---

### Post by superprash2003 on 2009-04-17
yes.. make sure the ip entered in the router settings , is the same as the ip you see when you type ifconfig in the ubuntu terminal

---

### Post by Nuticulus on 2009-04-19
I set the right ip address, and it's still not working. Is a router restart necessary?

---

### Post by MaindotC on 2009-04-20
Look let's see if the router is the problem.  First of all, just wire into your connection from the ISP.  If that's not possible, disable the firewall on your router and restart your torrent thing.  If you can get all you need with the router either removed or the firewall on the router removed then we know where to troubleshoot.

---

