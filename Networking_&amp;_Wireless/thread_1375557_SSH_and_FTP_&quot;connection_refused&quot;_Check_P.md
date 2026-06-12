---
title: "SSH and FTP &quot;connection refused&quot; Check Point router"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by kazec on 2010-01-08
I have a new server running on xubuntu 9.10 behind a "Check Point Safe @ Office security appliance" (a LAN switch with an obnoxious firewall), and cannot make ssh, ftp, telnet, or vnc connections to it from outside the network. All I get are "connection refused" errors. I've made sure sshd, x11vnc, and proFTPd are running when I test the connections, and that ufw (firewall) has all of their default ports completely unrestricted. I've set a rule on the router to allow and forward all connections and all ports to the server, and I've also also put it on the exposed machines list, which reads like it should provide full access to any incoming connection. I still can't make connections to it, and it's driving me nuts. Does anyone have suggestions (or requests for more information)?

Thank you so much!

(ps- The router isn't really a choice: even if I bought another, I'd have to hide it and hope no one notices the policy breach)

---

### Post by Dysport on 2010-01-08
Have you considered to completely turn off ufw [sudo ufw disable]? Why forward all ports to the server and expose the host when you can just open the ports you need (21,22,5900) in your hardware firewall?
Also if you open port 22 (or 21 for that matter) to the internet I strongly recommend a brute force protection with iptables:
```
sudo iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
sudo iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 8 --rttl --name SSH -j DROP
```

---

