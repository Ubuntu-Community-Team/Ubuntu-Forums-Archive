---
title: "service command for network restart does not work lucid 64 bit properly"
date: 2011-03-13
forum: Networking &amp; Wireless
---

### Post by jamesbon on 2011-03-13
Here is a situation when I do 
```
root@bond:~# service networking restart
restart: Unknown instance: 

```
and when I do 
```

root@bond:~# service networking stop
stop: Unknown instance: 

```

now if I do 
```
 /etc/init.d/networking stop
 * Deconfiguring network interfaces...       Ignoring unknown interface eth1=eth1.
                                                                                                                                                                [ OK ]


```
note above I did not used service command and it shows working.

and now if I start it in same way I get a warning.
```
/etc/init.d/networking start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service networking start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start networking
networking stop/waiting

```
In any case either service command or using /etc/init.d/networking with restart does not do any thing.
It does not work and neither does it start.Is it ia problem with Ubuntu 10.04 that service utility does not work properly?

---

### Post by dgray_from_dc on 2011-03-14
I too am having that problem only I'm working in Lucid 32-bit.  I've in fact run into an issue where my networking service (working with no problems before, and completely unchanged) will not start on boot as it normally did just a few days ago.

I've tried starting it manually, only for the service command to tell me that it is stopped/waiting.  I ran across this thread while trying to figure out how to start it up manually since the service command doesn't seem to work.

---

### Post by PatrickChapman on 2012-01-05
The "instance" is which interface you want to start. Try something like:
> sudo service networking start INTERFACE=eth0
which is simular to
> sudo start networking INTERFACE=eth0
and
> sudo initctl networking start INTERFACE=eth0

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

