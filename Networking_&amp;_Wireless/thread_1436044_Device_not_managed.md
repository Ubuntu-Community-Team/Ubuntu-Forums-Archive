---
title: "Device not managed"
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by adeelm on 2010-03-22
hi,
       I have recently installed ubuntu 9.10 and I have facing an issue regarding the network cards installed. They are not shown in it. It says that device not managed. I have two Network Interface cards and both are not warking. I have given the ip addresses in the /etc/network/interfaces file and also the namesever in resolv.conf file. When I try to start the networking service it gives the message given below.

infosec@Tulip:~$sudo service networking start
networking stop/waiting
infosec@Tulip:~$ sudo service networking restart
restart: Unknown instance: 

when I try to do restart it using /etc/init.d/ it again gives same messages...

infosec@Tulip:/etc/init.d$ sudo ./networking start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service networking start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start networking
networking stop/waiting
infosec@Tulip:/etc/init.d$ sudo ./networking restart
 * Reconfiguring network interfaces...                                                                                                                [ OK ] 
infosec@Tulip:/etc/init.d$


after this I can not ping any of my lab machines.

Please need your help.

Thanks
Adeel

---

### Post by adeelm on 2010-03-22
hi,
    I have been working on this issue, I have made some changes but they did not effected. Now I can see ifupdown eth0  and ifupdown eth1 in the network manager. As well as I can see the Auto eth0 and Auto eth1.

I can change the settings of Auto eth0 and Auto eth1 using the network manager but I can not edit the settings of ifupdown eth0 and ifupdown eth1.

Need you help in this manner.

Thanks
Adeel

---

### Post by Iowan on 2010-03-23
> **adeelm said:**
> It says that device not managed. I have two Network Interface cards and both are not warking. [COLOR="Red"]I have given the ip addresses in the /etc/network/interfaces file [/COLOR]That would be why Network Manager doesn't manage them.

---

### Post by adeelm on 2010-03-24
[[COLOR=#339900]**hi Iowan,**[/COLOR]]("http://ubuntuforums.org/member.php?u=65323")

Thanks. I removed the entries in the /etc/network/interfaces file and also removed the changes I made in the /etc/NetworkManager/ files. Now I do not see the ifupdown eth0 and ifupdown eth1 in the network manager. but I still can not restart the networking service.

I have tried it using the following ways.

1.   service networking restart
2.   /etc/init.d/networking restart
3.  restart networking

Please need your help...

Thanks.
Adeel

---

### Post by Iowan on 2010-03-24
You will probably need to restart Network Manager as well. To keep everything properly synched, I usually just reboot the machine.

---

### Post by adeelm on 2010-03-26
hi Iowan,

Thanks a lot. I restarted the machine and it worked. Now I am on the network and its working fine now.

Thanks
Adeel

---

### Post by Iowan on 2010-03-26
Glad you got it going. :D
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---

