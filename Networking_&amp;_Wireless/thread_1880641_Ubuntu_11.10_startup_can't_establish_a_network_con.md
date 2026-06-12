---
title: "Ubuntu 11.10 startup can't establish a network connection and just hangs"
date: 2011-11-14
forum: Networking &amp; Wireless
---

### Post by arnorhs on 2011-11-14
I'm running ubuntu 11.10 through virtualbox on a Mac OSX snow leopard host.

I've been running it only for a few days with no problems, initially.

All of a sudden I'm having problems starting the virtual machine with a network adapter. I hadn't changed anything except I ran apt-get upgrade, which might have upgraded something in the network adapter.

These are the errors I'm getting at startup:
[IMG]http://i.stack.imgur.com/70RVh.png[/IMG]

The virtual machine simply hangs there for a couple of minutes while trying to find the adapter or network. The host network is working fine, as you can see by me posting this here.

I googled around and found this thread: [http://ubuntuforums.org/showthread.php?t=1859432](http://ubuntuforums.org/showthread.php?t=1859432)

But I wasn't actually upgrading from another version of Ubuntu, but I tried the proposed solution anyways and I didn't have any luck. (the files were already there)

Oh, btw:
- ifconfig only shows the loop back device: [http://cl.ly/2v0u460P0N1Y1v1m3m1G](http://cl.ly/2v0u460P0N1Y1v1m3m1G)
- /cat/network/interfaces shows the correct interfaces: [http://cl.ly/0X1F31472K2o09050M08](http://cl.ly/0X1F31472K2o09050M08)

One thing that's super weird is that after disabling the adapter in virtualbox, the error persists.

Any ideas?

---

### Post by arnorhs on 2011-11-15
So is this post moderated, or is this just such an unusual error?

---

### Post by hansdown on 2011-11-15
> **arnorhs said:**
> So is this post moderated, or is this just such an unusual error?

Welcome to the forum,arnorhs.

Yes, to both of your replies.

The posts are moderated, and the error, may be somewhat, troublesome.

My post, will help "bump" your post, so that, you can get help. :D

---

