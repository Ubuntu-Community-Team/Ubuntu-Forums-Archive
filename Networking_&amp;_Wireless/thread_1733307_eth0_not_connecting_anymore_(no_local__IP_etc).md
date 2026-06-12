---
title: "eth0 not connecting anymore (no local  IP etc)"
date: 2011-04-19
forum: Networking &amp; Wireless
---

### Post by Occi on 2011-04-19
Hi

I've just set up some old hardware mixed with Ubuntu 10.10, and  I'm going to use it as a server.

**What I have done:**
- installed php, mysql, apache, ssh, openssh
- updated ubuntu (lots of checkbox', didn't read all of them)
- let ubuntu recognize drivers, as far as  I can see, it only updated the GPU
- set up ssh, and remote desktop
- ^tested and working from mobile
- installed firestarter (firewall)
- still working
- opened port on the router, rebooted it
- if I remember correct, I still had internet (it was late at night..)
- shut down computer

= suddenly not connecting

I'm positive that the cable works, I'm using it with my laptop as we speak. So I'm guessing it's either settings on Ubuntu, or router denying it, somehow..

**What I have tried:**
- sud /etc/init.d/networking restart; sudo dhclient
This actually lets ubuntu get a local IP for about 2 seconds, and then it disconnects again. The local IP is the same as before I encountered problems, so it would probably be ok.

- if I do ifconfig -a it shows both "eth0" and "lo". I have no idea what and where this "lo" came from, and I have not touched it. "lo" do have a local inet addr  (127.0.0.1), but "eth0" does not (only for 2 seconds when restarting).


I've been googling like a madman, but can't seem to find anything just like this.

Thanks.


[B]*** EDIT ***

I just remembered that I tried "sudo whoami" from my mobile last night, and since it wasn't installed I did "sudo apt-get install whoami" for test. So I uninstalled it now, and that seems to have fixed it. Could it be that simple, a bug, or was it maybe the reboot that did the fix. :\ 

I'm letting the thread stay, so others may find my "fix"..
[/B]

---

