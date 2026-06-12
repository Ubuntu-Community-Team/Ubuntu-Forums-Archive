---
title: "Uncomplicated Firewall"
date: 2011-07-02
forum: Networking &amp; Wireless
---

### Post by amryehia on 2011-07-02
[FONT=Times New Roman][SIZE=3]i enable firewall "ufw"

# ufw enable
then this firewall blocked telnet and http traffic

now i want configure it 
as 
iptables -A FORWARD -p tcp --dport 80 -j ACCEPT
iptables -A FORWARD -p tcp --dport 23 -j ACCEPT
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -p tcp --dport 23 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 80 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 23 -j ACCEPT

how can i do it using " ufw" ???
and what best firewall 
and is this information right
[FONT=&quot](important note: UFW is not the firewall. UFW just configures your iptables)[/FONT][/SIZE][/FONT]???

---

### Post by Dangertux on 2011-07-02
> **amryehia said:**
> [FONT=Times New Roman][SIZE=3]i enable firewall "ufw"

# ufw enable
then this firewall blocked telnet and http traffic

now i want configure it 
as 
iptables -A FORWARD -p tcp --dport 80 -j ACCEPT
iptables -A FORWARD -p tcp --dport 23 -j ACCEPT
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -p tcp --dport 23 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 80 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 23 -j ACCEPT

how can i do it using " ufw" ???
and what best firewall 
and is this information right
[FONT=&quot](important note: UFW is not the firewall. UFW just configures your iptables)[/FONT][/SIZE][/FONT]???

You are correct -- UFW only configures your iptables rules, however if you try to use say a normal iptables script AND UFW then UFW tends to overwrite your rules. You can use iptables scripts as normal WITHOUT UFW. Or, you can add the same rules to UFW like so.

```

ufw allow 80/tcp 

```This will allow port 80/tcp on any interface.

You can further specify say something like this

```

ufw allow from 192.168.0.3 to 192.168.0.5 port 80 proto tcp

```This would allow traffic from 192.168.0.3 destined to 192.168.0.5:80/tcp . You could also substitute any for either address. You can also use CIDR to denote multiple addresses as well. Consult the docs for more information.

---

### Post by claracc on 2011-07-03
You can install gufw (sudo aptitude install gufw), the gui to configure ufw in an easy way.

Then, you select the add button to put the rules you want to control traffic.

---

