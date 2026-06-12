---
title: "Ignoring unknown interface eth0=eth0"
date: 2010-11-05
forum: Networking &amp; Wireless
---

### Post by wznjsy on 2010-11-05
I want to edit my hosts file, so I.
sudo gedit /etc/hosts
I saved, and reset the network by
sudo /etc/init.d/networking restart

but got output of:

 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.

and hosts file doesn't work for me.
What's wrong? How to solve it.

I am using ubuntu 10.10 now.

---

### Post by chili555 on 2010-11-05
Generally, that message is thrown out when there is a listing in /etc/network/interfaces for an interface that is not up. For example, if there is no ethernet cable attached because you are intending to use wireless, eth0 will not be brought up because it's not capable of making a network connection.

The message is mostly harmless; it's not an error or even a warning; it's an 'ignore.'

Network Manager manages interfaces which are ***not*** in /etc/network/interfaces. If, like in my laptop, there is a good, working wireless connection, it doesn't really matter whether NM is handling eth0 or not. If you are fastidious, like me, you can certainly edit /etc/network/interfaces to remove the eth0 entries. Above all else, don't mess with lo.

Of greater concern, may we help you with your /etc/hosts? What are you trying to do and how have you edited the file so far?

---

### Post by wznjsy on 2010-11-05
> **chili555 said:**
> Generally, that message is thrown out when there is a listing in /etc/network/interfaces for an interface that is not up. For example, if there is no ethernet cable attached because you are intending to use wireless, eth0 will not be brought up because it's not capable of making a network connection.

The message is mostly harmless; it's not an error or even a warning; it's an 'ignore.'

Network Manager manages interfaces which are ***not*** in /etc/network/interfaces. If, like in my laptop, there is a good, working wireless connection, it doesn't really matter whether NM is handling eth0 or not. If you are fastidious, like me, you can certainly edit /etc/network/interfaces to remove the eth0 entries. Above all else, don't mess with lo.

Of greater concern, may we help you with your /etc/hosts? What are you trying to do and how have you edited the file so far?

Thanks for your message. I opened my file  /etc/network/interfaces but no eth0 entry. it shows:

auto lo
iface lo inet loopback


I attach my file /etc/hosts for your info.

166.166.166.52	scott-Inspiron-1420	# Added by NetworkManager
127.0.0.1	localhost.localdomain	localhost
::1	scott-Inspiron-1420	localhost6.localdomain6	localhost6
127.0.1.1	scott-Inspiron-1420

174.36.30.67 dropbox.com
174.36.30.71 [www.dropbox.com](www.dropbox.com)
75.101.129.115 dl.dropbox.com
75.101.159.151 dl-web.dropbox.com
174.36.30.67 forums.dropbox.com





# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by chili555 on 2010-11-05
What about it doesn't work as expected? After I amended my /etc/hosts, it seems to work for me:>  ping -c3 dropbox.com
PING dropbox.com (174.36.30.67) 56(84) bytes of data.
64 bytes from dropbox.com (174.36.30.67): icmp_req=1 ttl=45 time=54.5 ms
64 bytes from dropbox.com (174.36.30.67): icmp_req=2 ttl=45 time=52.4 ms
64 bytes from dropbox.com (174.36.30.67): icmp_req=3 ttl=45 time=53.3 ms

--- dropbox.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 52.444/53.453/54.586/0.918 ms


---

### Post by wznjsy on 2010-11-05
> **chili555 said:**
> What about it doesn't work as expected? After I amended my /etc/hosts, it seems to work for me:


i do not know. 

I reset the network by
sudo /etc/init.d/networking restart

but got output of:

* Reconfiguring network interfaces... Ignoring unknown interface eth0=eth0.

i guess you did not get this message. So it works for your computer

---

### Post by chili555 on 2010-11-06
As I said, it's not an error. My question is that you apparently amended /etc/hosts to direct traffic to specific IP addresses. Is it doing so as you wished? If so, I think it is working.

Your system is already ignoring an unknown interface; it is safe for you to ignore it, too.

---

