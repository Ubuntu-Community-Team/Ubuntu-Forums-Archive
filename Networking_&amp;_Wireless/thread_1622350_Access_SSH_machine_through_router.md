---
title: "Access SSH machine through router?"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by xiainx on 2010-11-15
Hi all,
I have two laptops with me here at school, one bigger one [home computer], and one smaller one [netbook]. I take the smaller one with me to class and when I'm out and about, however, I keep all of my things on the bigger one. I would really like to be able to set up some sort of SSH port forwarding for the bigger machine so that, when I'm out and I realize I left file X on my home machine, or I want to listen to a certain song, or whatever, I can just scp it to the netbook.
The issue is, at my dorm, I'm stuck behind a firewall and can't just set up a SSH daemon and port forward through the router, I need a more clever solution. I do have a home server (not with me at school), which I commonly use for transferring files.
Basically, I'm wondering if there is some way I can SSH into my server box, with reverse port forwarding so that, when I am out and about, I can just log into my server and copy files from my home computer for use on my netbook.
I've tried a couple of solutions which come up from google "reverse ssh" but haven't been able to get them to work. A step by step guide to doing this would be great. Again, the setup is:
Home server [ssh-able]
Home Computer [behind firewall, can't ssh into at the moment]
Netbook []
Want to be able to SSH from Netbook to Home computer, probably using Home server.

---

### Post by puppywhacker on 2010-11-15
From your homecomputer, make a reversed tunnel to your homeserver.
```
ssh -R 2200:localhost:22 xiainx@homeserver.com
```

Check if your port is now listening
```
netstat -na | grep 2200
```

Check if you can now ssh back into the reversed tunnel with:
```
ssh -p 2200 xiainx@localhost
```


Now from your notebook ssh to homeserver with a forward tunnel
```
ssh -L 22:localhost:2200 xiainx@homeserver.com
```

Now you can on your netbook scp to localhost and it will tunnel through the forward tunnel to the homeserver and through the backward tunnel into your laptop.

Ofcourse you can after creating the backward tunnel also log in to your homecomputer and create a second backward tunnel into your netbook, that is if your netbook is not behind a NAT as well. That way, not all your traffic routes through your homeserver, you only use it as a jump-on point to connect to your homecomputer remotely.

---

