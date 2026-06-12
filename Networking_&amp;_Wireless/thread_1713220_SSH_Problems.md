---
title: "SSH Problems"
date: 2011-03-23
forum: Networking &amp; Wireless
---

### Post by Fujiwara86 on 2011-03-23
I have a problem using SSH in Ubuntu 10.10.

Previously, I could SSH from my (wireless) laptop into my desktop and from my desktop into my laptop no problem. Both computers are running Ubuntu 10.10, Desktop 64 bit version, Laptop 32 bit version.

However, since a recent update, the SSH no longer works.

If I try to log into my desktop from my laptop, I receive the error "no route to host". Pinging my desktop receives no response. 

If I try to log into my laptop from my desktop I get the error "key verification failed". However I do get a response when pinging my laptop from my desktop.

On both machines internet works fine and I get a response pinging the gateway.

If someone could help me out, that would be great! Please bear in mind I'm still a Linux noob...

Thanks.

---

### Post by Fujiwara86 on 2011-03-24
bump

---

### Post by jerome1232 on 2011-03-24
Okay, so first can you ssh into localhost on both machines?

```
ssh localhost
```


If that works then you know at least openSSH server is working correctly on both machines.

Second double check and make sure you have the right IP's for both machines, check with ifconfig.

Is there a possible reason for your laptop to have changed it's host key? Such as reinstally ssh server or something? If there is and you know your laptop's host key has in fact changed, go ahead and delete the file .ssh/known_hosts on your desktop then reattempt logging in via ssh.

Post back with your results, make sure to note the ip's of both machine's, perhaps posting the exact error messages you get if you get them.

---

