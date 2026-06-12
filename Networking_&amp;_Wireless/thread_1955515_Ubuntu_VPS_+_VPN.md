---
title: "Ubuntu VPS + VPN"
date: 2012-04-09
forum: Networking &amp; Wireless
---

### Post by kingv on 2012-04-09
Hello everyone!

I've got a 10.04 VPS with a pptp server running. I can connect to it without any issues. I can even use a browser, but when visiting https sites it goes nowhere. Any idea why this is? I've followed the steps from below and everything went smooth besides this https thing. Any clues?:) 

Thanks!

```
apt-get install pptpd
Once it is installed, let’s create user accounts for your VPN server by editing the chap-secrets file. Use any editor you like, I personally prefer Nano.
nano -w /etc/ppp/chap-secrets
Each users should be added in new line with following structure
yourusername pptpd yourpassword *
Next step is to configure localip/remoteip assignment on pptpd.conf
nano -w /etc/pptpd.conf
Since my local router is on 192.168.0.1, I wanted to avoid using the same IP assignment for my VPN connection. so I’m using 192.168.111.xxx instead on pptpd.conf
localip 192.168.111.1
remoteip 192.168.111.234-238,192.168.111.245
Now, let’s get IP forwarding working by editing sysctl.conf file
nano -w /etc/sysctl.conf
then uncomment this line
net.ipv4.ip_forward=1
Save the file and reload the configuration.
sysctl -p
Next is to edit rc.local file for iptables rule
nano -w /etc/rc.local
Add these line right above exit line. (eth1 is my public ethernet port, adjust as needed)
iptables -t nat -A POSTROUTING -s 192.168.111.0/24 -o eth1 -j MASQUERADE
iptables -I FORWARD -p tcp -syn -i ppp+ -j TCPMSS -set-mss 1356
Last but not least, let’s define the DNS to use with our pptpd. Currently I’m using Google Public DNS – It is fast and reliable; I know some of you prefer OpenDNS.
nano -w /etc/ppp/options
Uncomment the entries with ms-dns 192.168.1.1 and 192.168.1.2 then replace the IP with Google Public DNS IPs so it look like this
ms-dns 8.8.8.8
ms-dns 8.8.4.4

ufw Masquerading
IP Masquerading can be achieved using custom ufw rules. This is possible because the current back-end for ufw is iptables-restore with the rules files located in /etc/ufw/*.rules. These files are a great place to add legacy iptables rules used without ufw, and rules that are more network gateway or bridge related.
The rules are split into two different files, rules that should be executed before ufw command line rules, and rules that are executed after ufw command line rules.

a) First, packet forwarding needs to be enabled in ufw. Two configuration files will need to be adjusted, in /etc/default/ufw change the DEFAULT_FORWARD_POLICY to “ACCEPT”: 
DEFAULT_FORWARD_POLICY="ACCEPT"
Then edit /etc/ufw/sysctl.conf and uncomment:
net.ipv4.ip_forward=1
Similarly, for IPv6 forwarding uncomment:
net.ipv6.conf.default.forwarding=1

b) Now we will add rules to the /etc/ufw/before.rules file. The default rules only configure the filter table, and to enable masquerading the nat table will need to be configured. Add the following to the top of the file just after the header comments:




# nat Table rules
*nat
:POSTROUTING ACCEPT [0:0]

# Forward traffic from eth1 through eth0.
-A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE

# don't delete the 'COMMIT' line or these nat table rules won't be processed
COMMIT
```

---

