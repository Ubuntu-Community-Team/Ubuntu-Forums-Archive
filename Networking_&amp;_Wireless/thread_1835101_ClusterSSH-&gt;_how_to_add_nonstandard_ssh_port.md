---
title: "ClusterSSH-&gt; how to add nonstandard ssh port?"
date: 2011-08-28
forum: Networking &amp; Wireless
---

### Post by kodb on 2011-08-28
I have  downloaded and installed ClusterSSH and have it working on all except one of the servers that uses a nonstandard ssh port.  I tried the usual syntax that would normally follow a ssh command:
```
 -P XXXX user@ipaddress
``` but when I run cssh it opens a window that tells me that it tried to connect the nonstandard port as user "XXXX" on port 22.
Has anyone ran into this and is there a syntax fix or did I miss something in the docs?
Thanks,
Bob

---

### Post by papibe on 2011-08-28
If that config line is making reference to ssh client's options, it should be:
```
-pXXXX user@ipaddress
```
Note the lowercase 'p'

Regards.

---

### Post by kodb on 2011-08-29
Ok, so I tried the syntax given above but no dice.  On re-reading the docs there is mention of using
```
 ipaddress:port
```

Sucess even using a preformatted cluster file to define the tags.
So, step by step to define and set up clusters
```
 sudo nano /etc/cluster
```

in /etc/cluster you define the cluster tag-> the name you'll give to the group of computers on your lan and what the addresses and ports are.  Assuming you are using an account that has administrative privileges, you don't have to define a separate user name.
So sample for my lan (I divided the clients and servers into separate groups to work with:
```
#ClusterSSH cluster and tags definition file
#you can put up to 30 ip addresses per line if I am reading the docs correctly
yourservergroupname  192.168.x.xxx 192.168.x.xxx
#if using nonstandard ports then use the below syntax
#yourservergroupname 192.168.x.xxx:xxx   where :xxx is the nonstandard port

#lines below for clients, use the same syntax as above if using nonstandard ssh ports
yourclientgroupname 192.168.x.xxx 192.168.x.xxx

```

Finally, to use simply invoke the following:
```
cssh yourservergroupname
```

This opens up the windows and you are good to go.

Hope this helps someone
Bob

---

