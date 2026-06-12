---
title: "How To Setup Two Apache Web Servers With One External IP Address"
date: 2010-12-09
forum: Networking &amp; Wireless
---

### Post by garryconn on 2010-12-09
I have two apache web servers and one static external IP address. Can anyone provide some advice on setting up both web servers to use the single IP address.

Example: 

External IP Address: 71.87.xxx.xxx >> Airport Extreme

Server Box #1: 192.168.0.100

-- domain1.tld
-- domain2.tld


Server Box #2:  192.168.0.150

-- domain3.tld
-- domain4.tld

The router I am using is an Apple Extreme (Yes, I know... sucks for this) With the research I have done, I have learned that I may have to use PAT (Port Address Translation). The Airport Extreme, from what I understand, do not support this. Only NAT.

Here's some links to posts I have found on the net that also explains further what I am aiming to achieve:

[LIST]
[*][http://www.apacheserver.net/Multiple-servers-1-IP-address-can-apache-do-to209311.htm]("http://www.apacheserver.net/Multiple-servers-1-IP-address-can-apache-do-to209311.htm")
[*][http://www.webmasterworld.com/apache/3308581.htm]("http://www.webmasterworld.com/apache/3308581.htm")
[*][http://serverfault.com/questions/107767/two-servers-two-domains-one-ip-mod-proxy-beginner]("http://serverfault.com/questions/107767/two-servers-two-domains-one-ip-mod-proxy-beginner")
[*][http://serverfault.com/questions/55846/running-multiple-publicly-accessible-web-servers-on-a-single-ip-address]("http://serverfault.com/questions/55846/running-multiple-publicly-accessible-web-servers-on-a-single-ip-address")
[*][http://ubuntuforums.org/showthread.php?t=1115636]("http://ubuntuforums.org/showthread.php?t=1115636")
[/LIST]


The more I'm researching I'm starting to think that "[Reverse Proxy]("http://en.wikipedia.org/wiki/Reverse_proxy")" is the solution I may need? Here's some links to articles I have read:

[list]
[*][http://www.server-world.info/en/note?os=CentOS_5&p=httpd&f=8]("http://www.server-world.info/en/note?os=CentOS_5&p=httpd&f=8")
[*][http://jeffbaier.com/articles/configuring-apache-virtual-hosts-for-nat/]("http://jeffbaier.com/articles/configuring-apache-virtual-hosts-for-nat/")  <<<--- SOLVED! :D
[/list]

---

