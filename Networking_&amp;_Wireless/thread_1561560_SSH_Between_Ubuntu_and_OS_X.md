---
title: "SSH Between Ubuntu and OS X"
date: 2010-08-26
forum: Networking &amp; Wireless
---

### Post by p.s. on 2010-08-26
I am trying to use ssh between my Ubuntu box and my Macbook. I'm completely new to ssh.

I am able to log into my Ubuntu machine from the macbook fine with the command:

ssh user@ipaddress

I messed around with it, sent a photo to myself with scp, looked through my files, etc.

When I reverse the process though, I'm not able to access the macbook from my ubuntu machine. I tried ssh -v and it seems like "port 22" is blocking me from doing it.

So of course I googled "open port 22 mac" to find out how to do it, but i ended up finding quite a few discussions about the dangers of having your port 22 open because it's the first place that people will look to see if your machine is there, after which they'll try to guess your pw using dict or etc.

So I have three questions:

1. How do I open port 22 from CL on the mac? (if anyone happens to know)

2. Should I open it, or is there a way to do it safely?

3. If it's a concern to open it on the mac, then does that mean it's already open on my ubuntu box because I *can* ssh into it, and should I close it?

---

### Post by arubislander on 2010-08-26
Simply opening port 22 will not get you far. You probably only have an ssh client on your Mac and to ssh from Ubuntu to your Mac you also need an ssh server. I don't have a Mac, so I can't help you there.

Now concerning the safety of opening port 22. What you read is true up to a point. If you are on your home network, then you'll probably have a router blocking access to your internal network from the internet. And unless you forward port 22 from your router to your Mac or your Ubuntu box, you needn't worry about it.

It's different of course if you connect to an untrusted wireless access point. But then a strong password is your main defense strategy. You could also configure your ssh server to use a port number other than 22. There are more ways of hardening your ssh server. But those are beyond the scope of this post.

---

### Post by p.s. on 2010-08-26
That basically answers my question. Thanks!

---

