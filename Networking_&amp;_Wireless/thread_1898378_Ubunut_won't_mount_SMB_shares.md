---
title: "Ubunut won't mount SMB shares"
date: 2011-12-21
forum: Networking &amp; Wireless
---

### Post by Macrotus on 2011-12-21
Hi all!

I have a several Windows shares mounted in my Ubuntu 11.10 x64. Sometimes they mount just well, but like now, only one of six is mounted. They are defined in the /etc/fstab. When I restart the computer, I can see all of them. sudo mount -a won't help. It says "host is down" but it's not. I can connect the shares always from my Windows machines.

---

### Post by Thylex on 2011-12-21
A couple of things to start with:

I'm gonna assume your firewall is configured to allow this kind of traffic, or turned off.

Once your ubuntu machine is up, can you confirm name resolution to the windows machine, both forward and reverse, ie by name and by IP?
Can you confirm IP connectivity by ping or similar?

If you are using cifs to mount, have you tried adding the workgroup name to the options?

What messages do you get from a manual mount, including any messages from the system log?

---

### Post by Macrotus on 2011-12-22
My firewall is configured right, I can do DNS lookups for the server and everything else is also right. 

I haven't tried the workgroup-option, our server is in domain.

---

### Post by Thylex on 2011-12-22
Then the workgroup name will be the same as the domain name. Worth a try, has helped us with similar problems many times in the past.

---

### Post by Macrotus on 2011-12-22
I added the workgroup option. Let's see what happens. I'll come back if it doesn't help.

---

### Post by Macrotus on 2012-01-04
It worked last week, but now it stopped working. I'm sure it's not releated to our Windows server, because all Windows machines can connect to it. Or then it's because of our server if it's discriminating Linux.

---

