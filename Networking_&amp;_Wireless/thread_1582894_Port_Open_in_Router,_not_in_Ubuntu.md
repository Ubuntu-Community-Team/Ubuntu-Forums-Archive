---
title: "Port Open in Router, not in Ubuntu"
date: 2010-09-27
forum: Networking &amp; Wireless
---

### Post by shkm on 2010-09-27
I have port 9001 forwarded through my router (Linksys WRT320N). This works perfectly in Windows, so obviously the router side is fine. In Ubuntu, however, I absolutely cannot get it to work.

[This site](http://www.yougetsignal.com/tools/open-ports/) reports it closed, and Transmission, the program I want to forward this port for, also reports it closed through its test feature.

I have not changed any firewall settings in Ubuntu whatsoever, and as I hear, nothing is firewalled by default. Transmission does appear to be listening on port 9001:

```

netstat -ntlup
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:9001            0.0.0.0:*               LISTEN      3157/transmission
udp        0      0 0.0.0.0:9001            0.0.0.0:*                           3157/transmission

```

Also, iptables:

```

sudo iptables --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   
```

I've searched around the Web and forums, but found nothing that could help. Running 10.04.

---

### Post by prshah on 2010-09-27
> **shkm said:**
> I have port 9001 forwarded through my router (Linksys WRT320N). This works perfectly in Windows, so obviously the router side is fine. In Ubuntu, however, I absolutely cannot get it to work.

Have you manually forwarded the port in the router's settings or are you using Windows uPnP to do it for you?

If you are using uPnP, please enable uPnP in Transmission as well (Edit-Preferences-Network-Use uPnP...).

You can check if you are using a firewall with "ufw"```
sudo ufw status
``` If you are running ufw, you can enable traffic across port 9001 with the command```
sudo ufw allow 9001
```

To know if ufw is blocking your port, check your dmesg (or /var/log/messages) for lines with the words "UFW BLOCK".

If you are using another firewall "frontend" such as firestarter, please use that to allow port 9001.

If uPnP does not work for you, perhaps you can manually forward port 9001 to your computer using the router's NAT facility. Remember that forwarding requires the correct IP address for your computer; the IP address may vary between Windows and Ubuntu depending on your setup.

Please post back with your results if you require more assistance.

---

### Post by shkm on 2010-09-27
Thank you for your response, prshah.

I am not using UPnP in Windows or Linux, and have manually forwarded the port in the router's settings (TCP & UDP as Transmission suggests). UPnP on the router side is enabled, so I tried turning it on in Transmission and restarting the client, but the port is still being reported as closed, and performance reflects this.

I just updated to Transmission 2.0.4 via their PPA to ensure that I'm all up to date, but this didn't help -- and I didn't expect it to, given that yougetsignal still reports the port closed.

The problem is fixed, however: forwarding port 55000 in exactly the same manner reports as open. 9001 simply will not. I have no problems switching to port 55000, though this does leave me wondering.

P.S. ufw is inactive.

---

