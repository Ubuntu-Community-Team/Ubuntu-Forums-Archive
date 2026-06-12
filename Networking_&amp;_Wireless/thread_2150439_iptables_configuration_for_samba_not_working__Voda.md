---
title: "iptables configuration for samba not working / Vodafone mobile - registration denied"
date: 2013-06-01
forum: Networking &amp; Wireless
---

### Post by huhh on 2013-06-01
Hello,


I am using Ubuntu 12.04 LTS and I have been trying to get iptables configured, to allow samba thru and see windows share in my local network. So far, I have documented on required ports and configuration, but nothing seems to work.
My iptables configuration is as follows:

[COLOR=#000000][FONT=Verdana]:INPUT DROP [0:0][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]:FORWARD DROP [0:0][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]:OUTPUT ACCEPT [8230:2502330][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]-A INPUT -i lo -j ACCEPT[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]-A INPUT -s 192.168.0.0/24 -p udp -m udp --dport 137 -j ACCEPT[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]-A INPUT -s 192.168.0.0/24 -p tcp -m tcp --dport 137 -j ACCEPT[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]-A INPUT -s 192.168.0.0/24 -p udp -m udp --dport 138 -j ACCEPT[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]-A INPUT -s 192.168.0.0/24 -p tcp -m tcp --dport 138 -j ACCEPT[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]-A INPUT -s 192.168.0.0/24 -p udp -m udp --dport 139 -j ACCEPT[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]-A INPUT -s 192.168.0.0/24 -p tcp -m tcp --dport 139 -j ACCEPT[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]-A INPUT -s 192.168.0.0/24 -p udp -m udp --dport 445 -j ACCEPT[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]-A INPUT -s 192.168.0.0/24 -p tcp -m tcp --dport 445 -j ACCEPT
COMMIT

The problem is I can access the network, I can see the workgroups (for Ubuntu and windows), I can access my Ubuntu via the network, but I cannot see the windows pc-s or the shares. If I allow traffic on the local network, everything works fine.
I have use this for local access: -A INPUT -s 192.168.0.0/24 -j ACCEPT, but since I am not at home, I do not wish to make this a permanent rule. 
I am certain there is another port that samba is using to connect to the windows pc-s, or I am doing something wrong. 

My other problem is I have plugged in my Huawei modem, i got prompted to introduce a PIN, I configured it and everything seemed to work fine, until I try to connect. When I try to connect, I get a message Mobile connection - disconnected (Modem network disconnected), but I shows the available network (Vodafone). I am on a postpaid plan and have tried all the settings.[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]

Can anyone help?[/FONT][/COLOR]

---

### Post by 2F4U on 2013-06-01
My understanding is that the ports need to be open for two-way communicaton.

[http://www.cyberciti.biz/faq/what-ports-need-to-be-open-for-samba-to-communicate-with-other-windowslinux-systems/](http://www.cyberciti.biz/faq/what-ports-need-to-be-open-for-samba-to-communicate-with-other-windowslinux-systems/)
[http://troy.jdmz.net/samba/fw/index.html](http://troy.jdmz.net/samba/fw/index.html)
[http://wiki.centos.org/HowTos/SetUpSamba](http://wiki.centos.org/HowTos/SetUpSamba)

Are the shares located on a Windows or a Ubuntu machine? Do the Windows machines have a firewall? Did you restart iptables after changing the rules?

---

### Post by huhh on 2013-06-04
The shares are on windows pcs (xp, 7) and are accessible from other windows pcs and even from my ubuntu pc when I allow everything on the local network, thus I think everything else is ok, except iptables. If I allow each port in iptables, it allows me to browse the network, workgroups, but it doesn't show the hosts. As soon as I change the rules to allow all traffic, that changes and everything works fine. I have read more on the subject and will continue to test until I find the sollution. Thanks for the links and I welcome any other ideas :)

---

