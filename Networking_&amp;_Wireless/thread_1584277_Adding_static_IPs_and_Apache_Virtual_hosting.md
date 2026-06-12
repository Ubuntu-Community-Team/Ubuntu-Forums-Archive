---
title: "Adding static IPs and Apache Virtual hosting"
date: 2010-09-28
forum: Networking &amp; Wireless
---

### Post by w1n78 on 2010-09-28
i'm running ubuntu 10.04 server 64bit. i need to add some static ips. i edited the /etc/networking/interfaces so it looks like this



iface eth0 inet static
  address xxx.x.xxx.31
  netmask 255.255.255.0
  network xxx.x.xxx.0
  broadcast xxx.x.xxx.255
  gateway xxx.x.xxx.75

iface eth0:1 inet static
  address xxx.x.xxx.43
  netmask 255.255.255.0
  network xxx.x.xxx.0
  broadcast xxx.x.xxx.255
  gateway xxx.x.xxx.75


then i restarted the service /etc/init.d/networking restart

i can ping it from the server but i can't ping it from another machine on the same network? i checked ufw and it's disabled. is there any other firewall configs i missed? is it a firewall issue? the first static ip works. i can ping it locally and on other machines. there are 2 websites hosted on the 1st ip. now i need to host other websites with their own ip.

please help.

---

### Post by lisati on 2010-09-28
My own preference is to set static IPs in my router rather than at Ubuntu's end, partly because it's sometimes easier, and partly because it can help avoid conflicts if you need to hook up your machine to someone else's network for some reason.

---

### Post by w1n78 on 2010-09-29
Thanks but unfortunately I don't have access to the router. The IT guys just give me IPs, dns info and gateway info. Any other ideas? I'm a noob to linux, kinda.

> **lisati said:**
> My own preference is to set static IPs in my router rather than at Ubuntu's end, partly because it's sometimes easier, and partly because it can help avoid conflicts if you need to hook up your machine to someone else's network for some reason.

---

### Post by w1n78 on 2010-09-29
i found the solution...

[https://answers.launchpad.net/ubuntu/+question/127339](https://answers.launchpad.net/ubuntu/+question/127339)

---

