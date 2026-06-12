---
title: "Networking init.d script for ICS"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by Rubedujour on 2009-11-06
Synopsis:I have a computer with two ethernet cards functioning as an internet gateway for a client pc.  I want to write an init.d script that turns the required services on at appropriate times

The long story:  I'm short on funds for another hub, but I had a second ethernet card and a lappy that needed a connection.  My ISP has long DHCP leases, and it's a pain to call them up to restore the connection after reconfiguring my network, so I came across a solution via [Ubuntu community documentation. :arrow:]("https://help.ubuntu.com/community/Internet/ConnectionSharing#Alternate%20gateway%20software%20%28GUI%29")  My primary ethernet card (now eth1) is connected to a cable modem, and my secondary (now eth0) shares that connection over routing by iptables with one client PC.   I also used dnsmasq to accomplish local DHCP/DNS.  

So, this all works great until either the host or the client hibernate, reboot, whatever, then I gotta retype the commands that re-enable this, because iptables rules flush and eth0 reconfigures itself to be useless.  Naturally, I thought a script the best way to accomplish it after reading that [other people had success with it. :arrow:]("http://ubuntuforums.org/showthread.php?t=300142")   Unfortunately the site with more detailed instructions referenced in that post is down.  Some of Firestarter's documentation is also currently down, and it's the only other workaround that I've seen that easily accomplishes the same thing.  So I'm writing my first init.d script, to accomplish bringing up the commands that make this setup work when the host box is on.  

From my understanding, init.d scripts run as root, so there's no need for sudo.   I took a guess that such a script would be dependent on /etc/init.d/network, but I don't know if I need to include $networking in the Required-Start as well.  I'm also not entirely sure that $remotefs is something I should include as Required-Stop or if I need default-start and -stop in the init info.  

I commented this file, perhaps excessively, because the upgrade to 9.10 reversed the eth0 and eth1 naming conventions, and I had to switch my /etc/dnsmasq.conf accordingly.  It was really confusing at the time, and I'd rather not forget how I did this later.   I am assuming that if I name this script eth0gw, make it executable, put it in /etc/init.d/ and then run "update-rc.d eth0gw", it will run this script when it comes on (from sleeping, hibernating, or boot) when networking does.   Am I correct?  This is my first init.d script and I'd hate to mess anything up implementing it, on account of the whole ISP DHCP lease annoyance.  If I've ignored any important conventions or there's something glaringly wrong, I'd love to know. 

#!/bin/sh -e
### BEGIN INIT INFO
# Provides: eth0gw
# Required-Start:    $network
# Required-Stop:     $network $remote_fs
# Default-Start:     
# Default-Stop:      
# Short-Description:Makes eth0 a DNS/DCHP enabled shared internet connection
### END INIT INFO

#This script makes eth0 a DNS/DCHP-enabled shared internet connection, 
#but it assumes that /etc/dnsmasq.conf has already been configured with the 
#appropriate interfaces, in this case eth0 as loal networking and eth1 as
#the connection to the internet. 

#assigns eth0 an ip address for local networking
ifconfig eth0 192.168.0.1
#allows forwarded packets (initial ones)
iptables -A FORWARD -i eth1 -o eth0 -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT
#allows forwarding of established connection packets (and those related to ones that started)
iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
#NAT 
iptables -A POSTROUTING -t nat -j MASQUERADE 
#Enable routing
sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

---

### Post by lensman3 on 2009-11-06
Go and down load the iptables script from Arno.

[http://rocky.eld.leidenuniv.nl/joomla/](http://rocky.eld.leidenuniv.nl/joomla/)

This will do everything that you want (and then some).  It has an active development listserv.  I use it on exactly the same setup that you do.

Hope this helps.

---

### Post by Rubedujour on 2009-11-06
Wow, thanks, I wish I'd culled google more carefully for something like this earlier.  I can definitely use this to accomplish what I want with less headache, I just need to take the time to configure it.   

Since I strained myself with all that painstaking copying and pasting though, would my original copypasta'd jobby have worked?  Or is it just a bad idea to use this sort of cobbled-together thing when there's alternatives under active development?

---

