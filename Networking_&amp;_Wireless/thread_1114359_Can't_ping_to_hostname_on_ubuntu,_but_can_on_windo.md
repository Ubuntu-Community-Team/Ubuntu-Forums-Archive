---
title: "Can't ping to hostname on ubuntu, but can on windows"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by lelizondob on 2009-04-02
I'm running Ubuntu Server on VirtualBox. The IP is 192.168.168.40 and the hostname is 'virtualserver', I can ping from the host machine (Ubuntu Hardy) to the Ubuntu Server using the ip, but if I ping to the hostname I get the "ping: unknown host virtualserver" error.

If I go to my web browser the same, I can't access [http://virtualserver](http://virtualserver), only [http://192.168.168.40](http://192.168.168.40)

The same with samba, I can't mount shares with the hostname, only with the ip.

But the weird thing is that windows can ping to the hostname from another machine to the virtualserver without a problem, windows can access samba shares with the hostname and even access [http://virtualserver](http://virtualserver) without a problem.

I've already edited all this:

/etc/hosts

127.0.0.1	localhost

127.0.1.1	virtualserver
192.168.168.40	virtualserver


/etc/resolv.conf

nameserver 192.168.1.254


/etc/hostname

virtualserver


/etc/dhcp3/dhclient.conf

send host-name "virtualserver";

but still, it's not working, what can I do?

Thanks in advance.

---

### Post by chili555 on 2009-04-02
> 192.168.168.40 virtualserverI think this line wants to go in the */etc/hosts* file of all the machines that want to ping or otherwise access *virtualserver* by name. My home server is *frankenputer* and so here is my *hosts* file:```
chili@LAPTOP60:~$ cat /etc/hosts
127.0.0.1	localhost.localdomain	localhost
127.0.1.1 LAPTOP60

192.168.1.101 frankenputer


# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by lelizondob on 2009-04-02
Thanks chili555, but that's exactly where I have it:

This is my /etc/hosts 
```

127.0.0.1 localhost
127.0.1.1 virtualserver
192.168.168.40 virtualserver

```

I forgot to add that I can't ssh to my virtualserver using the hostname, only my ip, but if I use putty, I can ssh username@virtualserver and username@ip

---

### Post by chili555 on 2009-04-03
> that's exactly where I have it:I'm sorry if I was not clear enough. The hosts file you've quoted is from the machine named *virtualserver*. I believe. What you want is for that line:```
192.168.168.40 virtualserver 
```to be in the hosts file of all the ***other*** machines. So, for example, if *sally-desktop* wants to access *virtualserver* by name, then the hosts file for *sally-desktop* must have the line in her hosts file.

I believe you can find a hosts file in Windows, too, although it has been quite a while since I used Windows '89!

The alternative is to install samba, bind and maybe a few other things and properly configure them, on all the Linux machines. One line in the hosts file seems a lot easier in a small environment, say 3-5 machines.

---

### Post by lelizondob on 2009-04-03
You really made my day. Thanks a lot, that worked.

One more thing, how to do this automatically? with samba?

---

### Post by chili555 on 2009-04-03
> **lelizondob said:**
> You really made my day. Thanks a lot, that worked.

One more thing, how to do this automatically? with samba?> The alternative is to install samba, bind and maybe a few other things and properly configure them, on all the Linux machines.It's not automatically installed and configured in Ubuntu because Ubuntu doesn't assume you will obviously be in a server-client environment where some of the machines are running Windows. It may also be a casualty of what will fit on an install CD.

I'm very glad it's working!

---

### Post by VicVega on 2009-09-20
> **chili555 said:**
> I'm sorry if I was not clear enough. The hosts file you've quoted is from the machine named *virtualserver*. I believe. What you want is for that line:```
192.168.168.40 virtualserver 
```to be in the hosts file of all the ***other*** machines. So, for example, if *sally-desktop* wants to access *virtualserver* by name, then the hosts file for *sally-desktop* must have the line in her hosts file.


chili555,
             Thank You! Thank You! Thank You! You rock :guitar:

I have spent the better part of the day reading tutorials and forum posts, trying to solve this problem, to no avail. After reading your post, I had my machines talking to one another on a first name (hostname) basis within minutes. Again, I thank you.

Dan

---

### Post by rockballad on 2010-05-04
Hello, I have the same problem. But your solution is not very clear to me :( May I ask again if I don't want to edit all related /etc/hosts files? Windows can ping those Ubuntu hostnames (I have several virtual Ubuntu machines). It may be because of DNS server. How can I setup the similar thing on Ubuntu machines? It's not very convenient to add static IPs to many /etc/hosts files. 

Thanks in advance.

---

