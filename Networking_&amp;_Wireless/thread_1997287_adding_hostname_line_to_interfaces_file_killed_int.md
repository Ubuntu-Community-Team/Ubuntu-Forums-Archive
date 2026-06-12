---
title: "adding hostname line to interfaces file killed internet"
date: 2012-06-05
forum: Networking &amp; Wireless
---

### Post by ekhatch1435 on 2012-06-05
ok i will try to keep this simple and still give you all the necessary information.

this pertains to ubuntu 12.04LTS server

before i did what i am about to say the internet worked like a charm.

long story short, i followed the advice on a forum where someone suggested that an easy way to be able to access a ssh host on a local lan network with a host name rather than an ip address (ie: user@server vs [email]user@192.168.1.xxx[/email]) was to simply add the line:

```
hostname yourhostnamehere
```

to the /etc/network/interfaces file.

i did this, then ran:

/etc/init.d/networking restart

after this the internet didnt work so i erased the hostname line i added to the interfaces file, 
sudo ifdown eth0
sudo ifup eth0

restarted the computer
restarted the modem/router

i have tried all the basic things that usually work but i am sure now that something got screwed up with the hostname, or hostname/network config files. im just not sure how to reverse it.  i tried searching google and these forums but "internet doesn't work"  is sort of on the general side of malfunctions.

any help would be appreciated. thanx

---

### Post by ekhatch1435 on 2012-06-05
ok i just reverted from static to dhcp back to static again and this fixed it

---

