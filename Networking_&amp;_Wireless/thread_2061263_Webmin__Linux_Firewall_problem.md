---
title: "Webmin / Linux Firewall problem"
date: 2012-09-22
forum: Networking &amp; Wireless
---

### Post by AvengerX9 on 2012-09-22
First I used the firestarter to control my firewall, but I think I wanna use the on in webmin instead, but after adding my first rule I ran into a problem.

> 
iptables-restore v1.4.12: 
The "nat" table is not intended for filtering, the use of DROP is therefore inhibited.


Error occurred at line: 9
Try `iptables-restore -h' or 'iptables-restore --help' for more information.



What does that mean ? The first rule is to block all access to the webmin port: 10000 except from one of my local network computers with IP 192.168.0.112

Hope someone can help a Linux newbie :)

---

### Post by AvengerX9 on 2012-09-22
UPDATE:

I changed the rule the other way around and the error is gone. From DROP to ACCEPT and from DO NOT EQUAL to EQUAL then my ip address and the port, but is that it ?

Is it that easy to add a rule that will allow incoming connections to my webmin on port 10000 only from the computer 192.168.0.112 or am I missing something ?

---

### Post by OrangeMadness on 2012-09-23
What the error message means:

NAT (Network Address translation):
Used to translate, or "redirect" if you like, a **public** IP address to a **local** network machine. 
For example: 
You own the public IP address 216.239.32.10
You have telnetd running on 192.168.0.100
You want to be able to reach 192.168.0.100 through the internet on telnet. Then you specify a NAT rule translating 216.239.32.10 to 192.168.0.100 locally so that when a telnet request arrives to your firewall it redirects it to the appropriate local machine.


I am not familiar with what you see in webmin firewall configuration and where you type your rule but it goes to the wrong place. Your rule is a filter and not a NAT, hence the error.


You can experiment with IPtables from console

```
iptables-save > ~/iptables 
```
This will dump all your iptables in a text file called iptables in your home directory

You will notice that the file has several sections 
*nat
*mangle
*raw
*filter
etc

Your rule should be under filter (currently it goes under *nat)

Add your rule under *filter and run:
```
iptables-restore < ~/iptables
```


There is a very good tutorial on iptables here: [[COLOR="Orange"]https://help.ubuntu.com/community/IptablesHowTo[/COLOR]]("https://help.ubuntu.com/community/IptablesHowTo")


Also you might want to check out Shorewall (iptables firewall interface - has also webmin module) at [[COLOR="Orange"]http://www.shorewall.net/[/COLOR]]("http://www.shorewall.net/")



:!: Do remember to keep a backup of your original iptables configuration (i.e iptables-save > ~/iptables.bak) before getting to work. 


Cheers.

---

