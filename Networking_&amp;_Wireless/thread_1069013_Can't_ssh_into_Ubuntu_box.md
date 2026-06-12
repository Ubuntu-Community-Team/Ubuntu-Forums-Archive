---
title: "Can't ssh into Ubuntu box"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by glenncvance on 2009-02-13
Hi everyone - I've set up ssh on a new install of II and am able to 'ssh localhost' just fine, but once I try to ssh into the box from my XP laptop (using winscp) I am unable to. I keep getting a message saying there is a network error.

I've confirmed that ssh is running with ps -ef|grep ssh -

```
root      4546     1  0 11:18 ?        00:00:00 /usr/sbin/sshd
```

and everything looks like it should be good to go, but nothing works. Does anybody have any ideas? Help a brother out? Thanks in advance.

---

### Post by Fire_Chief on 2009-02-13
Make sure Ubuntu does not have its firewall enabled

```
sudo /etc/init.d/ufw stop
```

---

### Post by glenncvance on 2009-02-13
```
sudo /etc/init.d/ufw stop
 * Skipping firewall: ufw (not enabled)...                               [ OK ] 

```

I'm a newb at the firewall. I'm guessing it's not enabled.

Thanks.

---

### Post by Fire_Chief on 2009-02-13
Can the XP box ping the Ubuntu box and vice versa?

---

### Post by glenncvance on 2009-02-13
Got it.

I can do it by IP but not by FQDN ( I set up a domain at dyndns.org ).

It works now. Many thanks Fire_Chief!

---

### Post by Dave_Man on 2009-02-15
Hi, 

I have the exact same problem, only in my case using the external IP doesn't work.
I can connect just fine using localhost or local IP but not using external IP.

Can anyone help?

Thanks.
Dave.

Fresh install of Intrepid 32bit.

---

