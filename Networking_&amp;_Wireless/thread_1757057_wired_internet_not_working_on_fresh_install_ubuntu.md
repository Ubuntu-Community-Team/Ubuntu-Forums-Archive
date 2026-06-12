---
title: "wired internet not working on fresh install ubuntu 10.10"
date: 2011-05-13
forum: Networking &amp; Wireless
---

### Post by priyamvaidya on 2011-05-13
hello everybody

i have a dual boot system with xp and ubuntu 10.10 (which i recently installed).  The internet works fine on my xp but on ubunutu it did not work.

i tried few things, like changing the proxy setting in mozilla firefox etc, but i did not work

i am attaching snapshot of ifconfig, resolve.conf and route-a commands for your referral 

[IMG]http://i1096.photobucket.com/albums/g321/priyamvaidya/ifconfig.png[/IMG]

[IMG]http://i1096.photobucket.com/albums/g321/priyamvaidya/resolvconf.png[/IMG]

[IMG]http://i1096.photobucket.com/albums/g321/priyamvaidya/route.png[/IMG]

help is appreciated

---

### Post by dineshs on 2011-05-13
route -n shows no default gateway.How did you configure the IP addresses manually or DHCP?

---

### Post by priyamvaidya on 2011-05-13
the ip is through dhcp.  i am getting the dhcp from my isp router.  when i am on the windows xp, internet is working fine with the same setting i.e. dhcp through router

---

### Post by dineshs on 2011-05-13
Can you try setting the IP manually via network manager?(set an IP outside DHCP range)
[http://ubuntuforums.org/showpost.php?p=9467538&postcount=5](http://ubuntuforums.org/showpost.php?p=9467538&postcount=5)

---

### Post by demilord on 2011-05-13
the nameserver seems weird it shouldnt be a local ip... but a outside ip..

---

### Post by priyamvaidya on 2011-05-13
@demilord

i am getting a dhcp from the router.  the ip you are seeing is that of the router.  i have setup the dns and gateway  in the router

---

### Post by priyamvaidya on 2011-05-13
dineshs

i tried what you told me but still there is no success

please find the snapshot of the lan configuration that i did

[IMG]http://i1096.photobucket.com/albums/g321/priyamvaidya/lanconnection.png[/IMG]

and also the snapshot of the route-n command after the lan configuration was done

[IMG]http://i1096.photobucket.com/albums/g321/priyamvaidya/route-n.png[/IMG]

---

### Post by dineshs on 2011-05-13
After doing LAN config pl run```
sudo service network-manager restart
```and see

---

### Post by priyamvaidya on 2011-05-13
it is giving error 
restart:unknown instance

---

### Post by dineshs on 2011-05-13
Just restart your PC and see

---

### Post by priyamvaidya on 2011-05-13
i did that, but still having the same problem

---

### Post by dineshs on 2011-05-13
still no gateway?Can you ping 192.168.1.1 ? What do you get for ```
cat /etc/network/interfaces
```
Note:While setting IP select one outside DHCP range (say 192.168.1.250)

---

