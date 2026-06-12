---
title: "Configure iptables for CISCO VPN Client"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by eugen_nicoara on 2009-01-29
Hi,

I have a question about CISCO VPN Client and iptables. I need to use CISCO VPN Client to connect to customer's VPN. Everything works fine with starting the service and opening the connection but when I try to open a ssh session it freezes end eventually it times-out. Of course, if I stop the iptables the ssh session works fine.

According to "VPN Client User Guide for Linux and Solaris v4.6", I should allow the following type of traffic to to pass through:
• UDP port 500
• UDP port 10000 (or any other port number being used for IPSec/UDP)
• IP protocol 50 (ESP)
• TCP port configured for IPSec/TCP
• NAT-T (Standards-Based NAT Transparency) port 4500

Here is what I've tried but without any result:
```
sudo iptables -A INPUT -p udp -s 0/0 -d 0/0 --dport 500 -j ACCEPT
sudo iptables -A INPUT -p udp -s 0/0 -d 0/0 --dport 10000 -j ACCEPT
sudo iptables -A INPUT -p udp -s 0/0 -d 0/0 --dport 4500 -j ACCEPT
sudo iptables -A INPUT -p esp -s 0/0 -d 0/0  -j ACCEPT
```

I know I'm missing something but don't know what. I use the client v4.8.02.

Thanks,
Eugen

---

### Post by NoReflex on 2009-01-29
Hello!

I also have a Cisco router running a VPN server but I never used Cisco's client. Instead I used vpnc (it's in the repos) and always worked perfectly. Maybe it can help you too.
Also I'm not sure I understand where you connect from and which computer you want to connect to. You use the VPN client to connect to the customer's VPN and then you try to connect to one of the machines in the VPN?

Best of luck!

NoReflex

---

### Post by casevh on 2009-01-30
A couple of ideas.

1) They may be using a port other than 10000. If they gave you a configuration file, it may list a different port number.

2) They may be using TCP/10000 instead of UDP/10000. Again, it would be listed in the configuration file.

If that does help, install Wireshark and capture the packets going through the physical interface. That should help you identify what needs to be allowed in through iptables.

casevh

---

### Post by eugen_nicoara on 2009-02-05
Thanks for replies. Indeed I have a configuration file (pcf file) and in that file the only two parameters that look interesting are *Host* (an IP address) and *TcpTunnelingPort=10000*. 
I tried opening that port for TCP protocol but that did not help at all. 

```
sudo iptables -A INPUT -p tcp -s 0/0 -d 0/0 --dport 10000 -j ACCEPT
```

I've never used Wireshark so I'd rather doubt it will help me. Anyway, I'll give it a try.

Another option would be to accept all traffic from that host but I don't like that option.

---

### Post by excalq on 2009-02-05
Try disabling the firewall temporarily (or at least to that host), and using the netstat command to see what ports are being used.

 ```
sudo netstat -npt
```

---

### Post by casevh on 2009-02-05
Enable UDP/10000, too. I know the configuration file says TCP, but that same port number is actually more commonly used as UDP.

casevh

---

### Post by eugen_nicoara on 2009-09-07
This is how I solved the problem: [http://ubuntuforums.org/showthread.php?t=159661]("http://ubuntuforums.org/showthread.php?t=159661")

---

