---
title: "SSH to server with multiple keys while retaining strict checking"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by The Altruist on 2009-11-28
OK, so my university's server has ssh, but with multiple rotating RSA keys.
You guessed it. I'm hitting the DNS SPOOFING warning.
I'd like to retain strict checking.
Assuming I get them in xx:xx:xx:xx:xx... format, what do I use to generate the appropriate entries in my known_hosts file?

---

### Post by Lars Noodén on 2009-11-29
They should provide you with an up-to-date set to add to your known hosts file.  Otherwise, you must verify the keys by hand.

You can assign multiple hostnames or ip addresses to the same key in /etc/ssh/ssh_known_hosts, for all users, or ~/.ssh/known_hosts for just you.  

```

server1,server2,server3 ssh-rsa AAAAB097y0yiblo97gvl...jhvlhjgluibp7y807t08mmniKjug...==

```

You can use globbing to a limited extent in either /etc/ssh/ssh_known_hosts or ~/.ssh/known_hosts.

```

172.19.40.* ssh-rsa AAAAB097y0yiblo97gvl...jhvlhjgluibp7y807t08mmniKjug...==

```

However, to get the effect you want, multiple keys for the same address, make multiple entries in either /etc/ssh/ssh_known_hosts or ~/.ssh/known_hosts, one for each key.

```

server1 ssh-rsa AAAAB097y0yiblo97gvljh...vlhjgluibp7y807t08mmniKjug...==
server1 ssh-rsa AAAAB0liuouibl kuhlhlu...qerf1dcw16twc61c6cw1ryer4t...==
server1 ssh-rsa AAAAB568ijh68uhg63wedx...aq14rdfcvbhu865rfgbvcfrt65...==

```

To get a pool of servers to share a pool of keys, you have to add each server-key combination manually

```

server1 ssh-rsa AAAAB097y0yiblo97gvljh...vlhjgluibp7y807t08mmniKjug...==
server1 ssh-rsa AAAAB0liuouibl kuhlhlu...qerf1dcw16twc61c6cw1ryer4t...==
server1 ssh-rsa AAAAB568ijh68uhg63wedx...aq14rdfcvbhu865rfgbvcfrt65...==

server2 ssh-rsa AAAAB097y0yiblo97gvljh...vlhjgluibp7y807t08mmniKjug...==
server2 ssh-rsa AAAAB0liuouibl kuhlhlu...qerf1dcw16twc61c6cw1ryer4t...==
server2 ssh-rsa AAAAB568ijh68uhg63wedx...aq14rdfcvbhu865rfgbvcfrt65...==

```

I'm not quite sure how to get that to work with hashed host names.  

**ssh-keyscan -t rsa *server1*** will get the rsa key for *server1*  
**ssh-keyscan -t rsa *server1* > *file*** put get the rsa key for *server1* in *file* (e.g. /tmp/z.key)


**ssh-keygen -l -f *file*** will give you a fingerprint for the key in that file

---

