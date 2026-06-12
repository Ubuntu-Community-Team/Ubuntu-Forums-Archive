---
title: "tversity via virtualbox"
date: 2007-12-01
forum: Multimedia &amp; Video
---

### Post by unabatedshagie on 2007-12-01
I have virtualbox installed fom the repo and have windows installed in a guest machine. 
 
What I would like to do is stream media from the windows guest to my xbox 360 using [tversity]("http://tversity.com/home/"). 
 
Through what I have been able to find on the net it seems I have to set up a bridged connection between ubuntu and windows. 
 
This is where I'm finding it hard to find information. 
 
It seems like it's possible but as of posting this I have been unable to find anyone that has posted detailed info on how to do it. 
 
I have read the virtualbox manual chapter on setting up bridging but if anything it has left me more confused than when I started. 
 
Could some kind soul give me a hand in setting up bridging between the host and guest?

---

### Post by Jose Catre-Vandis on 2007-12-01
Have a look here:

[http://bimma.me.uk/2007/09/30/ubuntu-creating-host-interface-networking-for-virtualbox/](http://bimma.me.uk/2007/09/30/ubuntu-creating-host-interface-networking-for-virtualbox/)

This connects your guest to the host network, which in turn should then allow you to do what you want

---

### Post by unabatedshagie on 2007-12-01
I seem to be having problems getting this to work.

I have installed everything and edited all the files.

I have changed the following:>  eth0 is your primary interface - change as necessary
with static ip 10.10.10.60 - change as necessary (changed to [COLOR=blue]192.168.0.2[/COLOR]) 
the bridge will have a static IP
you will have all tap interfaces using a static IP
user=bimma (changed to [COLOR=blue]alex[/COLOR])The only thing I'm not sure about is the static ip, should that be the ip address that the host machine is using (I have my router configured to always give this machine 192.168.0.2) or a different one like 192.168.0.3?

---

### Post by Jose Catre-Vandis on 2007-12-02
> **unabatedshagie said:**
> I seem to be having problems getting this to work.

I have installed everything and edited all the files.

I have changed the following:The only thing I'm not sure about is the static ip, should that be the ip address that the host machine is using (I have my router configured to always give this machine 192.168.0.2) or a different one like 192.168.0.3?

That's right. The bridge interface takes over your machine IP, so you use your machine IP in the config: 192.168.0.2 in your case

---

