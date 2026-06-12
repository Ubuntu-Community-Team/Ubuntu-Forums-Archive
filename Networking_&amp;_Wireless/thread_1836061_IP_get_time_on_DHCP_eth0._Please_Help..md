---
title: "IP get time on DHCP eth0. Please Help."
date: 2011-08-30
forum: Networking &amp; Wireless
---

### Post by pedroo84 on 2011-08-30
Hello, my name is Pedro and I'm from Brazil.
I have a very unusual question that maybe you guys could help me with.
I've set up a computer running Ubuntu to be a streaming server (it runs Wowza Streaming server)
Inside the computer case I've installed a internet router that is powered by the 12v computer source, so that when the computer shutdown the router also shutdowns and vice versa.

The problem is: This router  takes about 2 - 3 minutes to boot up, and Ubuntu is way faster, so that when the computer logs in it tries to get IP trough DHCP on eth0 for a few seconds and it fails (because the router is not yet booted) If I wait a few moments and go to the network menu and click on eth0  it gets the IP and starts to work, but it's a process that have to be done manually. My problem is that this computer is running remote and I intent to access it via VNC.

What I want is: either to delay boot process or increase the time that Ubuntu tries to get the IP on DHCP.

Does any one know if this is possible?
thank's in advance.

---

### Post by spiky001 on 2011-08-30
There was a fix for this awhile ago, There was a script written I have been trying to find it, Maybe the Person who wrote or Used it will spot this post, I will google some more, so dont give up.

---

### Post by pedroo84 on 2011-08-30
I've searched too, but with no luck.
If anybody knows how do fix I would be grateful .
thanks

---

### Post by spiky001 on 2011-08-30
Do you still connect to the router with eth0 cable?

---

### Post by pedroo84 on 2011-08-30
Yes, eth0 is connected via cable to the router (which gives ip trough DHCP)
I found this: could it work?
[http://osdir.com/ml/networkmanager-list/2010-01/msg00063.html](http://osdir.com/ml/networkmanager-list/2010-01/msg00063.html)

---

### Post by spiky001 on 2011-08-30
A script would be easy if I knew how to right 1 and where to install it. I ran a script once which turned eth0 off for set time then restarted it, but it was not automated, it,s the automated part you need, it has to be set in a file that it reads at boot.

---

### Post by spiky001 on 2011-08-31
Ok I have done something hope it,s what you want.```
gksudo gedit /etc/rc.local
```Then at the end before "exit 0" type

ifconfig eth0 down
sleep 120
ifconfig eth0 up

Save and exit reboot the eth0 should not be connected until 120 secs is up then eth0 should connect

---

