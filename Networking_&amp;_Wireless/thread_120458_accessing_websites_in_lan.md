---
title: "accessing websites in lan"
date: 2006-01-21
forum: Networking &amp; Wireless
---

### Post by kasemodz on 2006-01-21
Hi, I have been running websites from ubuntu server. I can access them by going typing the ip address but I would like to change that address to a name. I know I can go to /etc/hosts and put that name there. However, this will only work with that computer itself. I wanted to make it so that any computer in my lan can connect to these websites with a name instead of the ip address? Is it possible to do that?

---

### Post by localzuk on 2006-01-21
Hi,

What you want to look at is running a DNS server. Take a look at a package called bind.

If the network is small and the IP of the server is not likely to change, it might be easier to just edit the hosts file of all the machines.

---

### Post by kasemodz on 2006-01-21
well localzuk the problem with that is that I have a laptop from school that is locked and I can only do what the school approves. OF course I can browse through the internet but not allowed to change any system files. So, I'll take a look at bind but adding this to host files is out of question.

---

