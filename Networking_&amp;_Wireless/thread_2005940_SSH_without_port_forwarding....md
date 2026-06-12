---
title: "SSH without port forwarding..."
date: 2012-06-18
forum: Networking &amp; Wireless
---

### Post by Mr.Dee on 2012-06-18
So I have my dad setup with an ubuntu netbook.  I would like to be able to ssh into it to fix any issues he might have.  His work involves traveling so he often logs in from a hotel wireless access point.  Would I be able to ssh to him?  I've done some research on this, but have not found anything solid.  
 
From what I do understand is that it would invole setting up a script on his end to connect to me, then I connect to myself...
 
Thanks in advance.

---

### Post by papibe on 2012-06-18
Hi Mr.Dee.

I don't think you would be able to do exactly that, but if ***you*** are 'ssh-accessible', I believe you can setup a reverse ssh tunnel to connect to your father's computer.

I works like this: your dad's run a script to reach you, and creates a port in your machine. After that, you can ssh to his computer using a special port in your own machine.

Take a look at this [article]("http://www.alexonlinux.com/reverse-ssh-tunnel-or-connecting-to-computer-behind-nat-router") for details. 

I hope that points you in the right direction, and tell us how it goes.
Regards.

---

### Post by sanderj on 2012-06-18
Two additional remarks:


You can also tunnel X sessions/program over a SSH:

```
ssh -X itsme@dadscomputer.com
```

then on dadscomputer type

```
firefox &
```



Furthermore, worth trying: install miredo (sudo apt-get install miredo) on both computers. Miredo will create an IPv6 tunnel over IPv4 through NAT.
If you put a "wget www.yourhost.com/hello-its-dad" into the crontab  running each 5 minutes, you can access your dad's computer over Ipv6.

---

