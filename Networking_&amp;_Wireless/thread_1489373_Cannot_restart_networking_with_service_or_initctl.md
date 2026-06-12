---
title: "Cannot restart networking with service or initctl"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by theneoindian on 2010-05-21
I cannot restart networking using service , initctl or start/stop/restart commands .
Anytime i use these commands :
```

sudo service networking restart
sudo restart networking 
sudo initctl restart networking

```
I get the following outputs , respectively :
```

restart: Unknown instance: 
restart: Unknown instance: 
initctl: Unknown instance:

```

But " **/etc/init.d/networking restart** " works ... 

This is the case with most of the services that 've been migrated to Upstart . 
As i understand , the upstart jobs must be controllable via *initctl / start / restart /stop* commands . 
The other services should be controllable via service command for sys v scripts . Please correct me if i'm wrong ...

*This however worked with Karmic , if i remember correctly ... *

---

### Post by abacate_vw on 2010-06-18
I can confirm this.

I'm using Ubuntu Server 10.04 64-bit.

---

### Post by freiquell on 2010-07-23
I have also no idea how I can ensure stop/start/restart on different distributions of Ubuntu/Dabian since I would like my .deb to run on all of them: [http://ubuntuforums.org/showthread.php?p=9597548](http://ubuntuforums.org/showthread.php?p=9597548)

---

### Post by dca on 2010-07-23
*/etc/init.d/service-name restart*
 
 Don't quote me but I believe you need 'chkconfig' package installed to use service restart commands...

---

### Post by PatrickChapman on 2012-01-05
The "instance" is which interface you want to restart. Try something like:
> sudo service networking restart INTERFACE=eth0
which is simular to
> sudo restart networking INTERFACE=eth0
and
> sudo initctl networking restart INTERFACE=eth0

---

### Post by capt_kirk on 2012-12-04
On 12.04 the following does not work:
```
sudo service networking restart INTERFACE=eth0
```
However, the following does work:
```
sudo service network-interface restart INTERFACE=eth0
```

---

