---
title: "SSH Tunneling Crossplatform"
date: 2012-07-17
forum: Networking &amp; Wireless
---

### Post by ubtBaba on 2012-07-17
Hi,

I had a question regarding SSH. In the past I have successfully setup SSH in my Ubuntu Machine and was able to connect VNC through the SSH tunnel.

I am now experimenting with my other computers which consists of Windows, Ubuntu and even OS X.

My question is can I use the machine running SSH server as a centralized place to authenticate SSH logins and then connect to my other computers on my home network for file transferring through a tunnel or do I need to run a SSH server on each machine?

I have a picture illustrating what I want to do.

Image Link: [http://postimage.org/image/mi58zww6d/](http://postimage.org/image/mi58zww6d/)
Mirror: [http://imageshack.us/photo/my-images/706/mynetwork.png/](http://imageshack.us/photo/my-images/706/mynetwork.png/)

---

### Post by The Linuxist on 2012-07-17
You can use the Ubuntu machine with the SSH server as a central place to forward connections to the rest of your machines.

From your Windows clients you can do this with Putty, by editing Connection -> SSH -> Tunnels.

From your Linux clients you can, for instance, setup forwarding for RDP[FONT=Ubuntu]

[/FONT]```
ssh -f user@ubuntu-ssh-server -L 3389:windowsmachine01:3389 -N
```

Such that you can then connect an RDP client on that machine to localhost and it will get forwarded to your windowsmachine01.

I'm pretty sure this is the same for the Mac, but I'm attracted to people of the opposite sex so I wouldn't know.

---

