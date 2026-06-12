---
title: "ubuntu 8.10 iptables 1.4.0.4 save ?"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by dondondon on 2009-03-24
[IMG]http://img.blog.yahoo.co.kr/ybi/1/b9/b4/ico1535ok/folder/3/img_3_1548_0?1237931062.jpg[/IMG]


Hi, can use iptables 1.4.0.4 products ..

South Korea is, I don

iptables 1.4.0.4

will inquire about the use of iptables

iptables-P INPUT DROP
iptables-P OUTPUT DROP
iptables-P FORWARD DROP

iptables-F

save is related inquiries
/ etc / network / interfaces
interfaces file
edit
post-down iptables-save-c> / etc / iptables.rules
has add

sudo sh-c "iptables-save> / etc / iptables.rules"

iptables-save

But

When you log out

Will restore all the original features

iptables-L

Search for it, but were unable to resolve

My thoughts ..

I want to save iptables rules
And DROP all the ports ..
Ports you want

I would like to open
ex>
ptables-A INPUT-p TCP - destination-port 80-j ACCEPT
iptables-A OUTPUT-p TCP - source-port 80-j ACCEPT

For questions about this issue, we will contact

Thank you, people do not speak English well Korea> 

---

