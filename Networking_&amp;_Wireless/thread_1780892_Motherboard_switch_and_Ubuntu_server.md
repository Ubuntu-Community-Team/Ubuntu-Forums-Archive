---
title: "Motherboard switch and Ubuntu server"
date: 2011-06-12
forum: Networking &amp; Wireless
---

### Post by tweaked on 2011-06-12
Hi all, I had to switch the motherbaord on my server box running Ubuntu Server 10.04 and am having some problems with the network. It took awhile to get things straightened out that the network is on eth2 now and I can get out from the server, but I cannot access it from outside. I get a "Failed to retrieve share list from server" error.
I am suspecting Samba but not sure. Where should I start looking?

Thanks,
tweaked

---

### Post by pqwoerituytrueiwoq on 2011-06-12
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/configuring-samba.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/configuring-samba.html)
maybe there

---

### Post by tweaked on 2011-06-12
I changed the network line in /etc/samba/smb.conf to reflect the change to eth2.
Is there anyplace else that might prevent me from seeing the server?

---

### Post by pqwoerituytrueiwoq on 2011-06-12
firewalls

---

### Post by tweaked on 2011-06-12
Hi all, I had to switch the motherbaord on my server box running Ubuntu Server 10.04 and am having some problems with the new network. It took awhile to get things straightened out that the network is on eth2 now and I can get out from the server, but I cannot access it from outside. I can see server in Windows Networks (but not Networks like before). I get a "Failed to retrieve share list from server" error.

I changed /etc/samba/smb.conf to reflect the change to eth2. Where else should I look?

---

### Post by uRock on 2011-06-13
Duplicate threads merged. Please do not create multiple threads on the same topic.

---

### Post by capscrew on 2011-06-13
> **tweaked said:**
> Hi all, I had to switch the motherbaord on my server box running Ubuntu Server 10.04 and am having some problems with the new network. It took awhile to get things straightened out that the network is on eth2 now and I can get out from the server, but I cannot access it from outside. 
What do you mean by "I can get out from the server, but I cannot access it from outside"?  Can you access this host from the LAN?> 

I can see server in Windows Networks (but not Networks like before). I get a "Failed to retrieve share list from server" error.

This can mean multiple things.  How about posting the results from the terminal using this ```
smbtree -d3
``` > 

I changed /etc/samba/smb.conf to reflect the change to eth2. Where else should I look?

What did you have to change?  Post the results of ```
testparam -s
```

---

