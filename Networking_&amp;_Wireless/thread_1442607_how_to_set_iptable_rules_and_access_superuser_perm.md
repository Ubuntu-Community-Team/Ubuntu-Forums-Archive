---
title: "how to set iptable rules and access superuser permission from web-based?"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by hong2010 on 2010-03-30
Hi friends..
i had wrote a network emulator program in c programming. It can run for ubuntu terminal with good performance. But i have to make it for web-based user configuration. So i had setup apache web server and write this program in cgi script and try to execute this program from web page. BUT IT CAN'T WORKS!!! 

This program must be run in root privilege($sudo -s) and add the iptables rules such as (#iptables -A OUTPUT -j QUEUE). So my question is how to add iptables rules in my cgi scripts? How to set the superuser(root privilege) permission to access my program through web server? Or any other method? your reply is highly appreciate... thanks..:P

---

### Post by iponeverything on 2010-03-30
Setup sudo for your apache user "www-data" with permissions for iptables and invoke it from the script with sudo.

---

### Post by hong2010 on 2010-04-09
> **iponeverything said:**
> Setup sudo for your apache user "www-data" with permissions for iptables and invoke it from the script with sudo.

Hi iponeverthing... i not quite understand how to setup sudo for apache, can you briefly explain the procedures? thanks...

---

