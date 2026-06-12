---
title: "network help please"
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by connor901 on 2009-01-30
hi i keep getting the could not resolve 'security.ubuntu.com' when trying to use sudo apt-get update

here is my /etc/hosts

cat /etc/hosts
127.0.0.1   localhost
127.0.1.1   Connors-Server.localhost.com Connors-Server

# The following lines are desirable for IPv6 capable hosts
::1    localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


i have changed the first two lines a little before to try and get it to work but havent found a fix yet any 1 else see something wrong or know what might be wrong

---

### Post by connor901 on 2009-01-31
Im sorry can we move this thread to the correct forum the server platform area

---

### Post by callan79 on 2009-01-31
> **connor901 said:**
> hi i keep getting the could not resolve 'security.ubuntu.com' when trying to use sudo apt-get update

cat /etc/hosts
127.0.0.1   localhost
127.0.1.1   Connors-Server.localhost.com Connors-Server


Hi connor901,

I don't think your hosts file really has anything to do with it. The hosts file is used for you to specify names of computers that don't exist on the Internet (ie on your local network).

So in order to connect to security.ubuntu.com, or ANY website or external server, you're going to need :

 -1- an IP Address
 -2- a subnet mask
 -3- a default gateway to the Internet (usually a modem/router)
 -4- at least one DNS server

You can test 1/2/3 by the command :
```
ifconfig
```

You can test 4 by the command :
```
cat /etc/resolv.conf
```

Also to show your network configuration :
```
cat /etc/network/interfaces
```

Can you paste the output of those three commands?

Thanks
CD

---

### Post by connor901 on 2009-01-31
i actually got it to work with a fresh install but if i run into a problem again i will post here

---

