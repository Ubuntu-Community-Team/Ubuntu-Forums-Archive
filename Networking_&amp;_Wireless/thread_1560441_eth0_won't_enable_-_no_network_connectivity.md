---
title: "eth0 won't enable - no network connectivity"
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by Dyno23 on 2010-08-24
Hello - Linux newbie.

Trying to get the wired nic working so I can troubleshoot the wireless.  I cannot get any kind of network activity.  

Been searching so I will post a little information that seems to be common with my situation. 

lshw -C network

reveals:

WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 00:11:11:3c:22:63
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:feaff000-feafffff ioport:ddc0(size=64)

ifconfig

reveals

lo   Link encap: Local Loopback
     inet addr: 127.0.0.1 Mask: 255.0.0.0
     inet6 addr:  ::1/128 Scope: Host
     UP LOOPBACK RUNNING MTU:16436 Metric: 1
     RX packets:12 errors: 0 dropped: 0 overruns: 0 frame: 0
     TX packets:12 errors: 0 dropped: 0 overruns: 0 frame: 0
     collisions:0 txqueuelen:0
     RX bytes: 720 (720.0 B) TX bytes: 720 (720.B)



Thanks for readin!

---

### Post by Dyno23 on 2010-08-24
It should be stated I have been doing a bit of configuring trying to get wireless to work based on this thread:

[http://ubuntuforums.org/showthread.php?t=1444746&page=3](http://ubuntuforums.org/showthread.php?t=1444746&page=3)

so there has been a bit of tinkering.

---

### Post by dtoronto on 2010-08-24
What does your /etc/network/interfaces look like?

---

### Post by Dyno23 on 2010-08-24
I type that, I get "access denied"

i sudo /etc/network/interfaces i get command not found

---

### Post by dtoronto on 2010-08-24
sorry,

```
cat /etc/network/interfaces
```

and post the output

---

### Post by Dyno23 on 2010-08-24
auto lo
iface lo inet loopback

---

### Post by Dyno23 on 2010-08-24
I don't appear to have network manager in the upper right either...fyi.

---

### Post by dtoronto on 2010-08-24
Ok, if your network is set up to administer an IP via DHCP, then you could try.

```
sudo nano /etc/network/interfaces
```

you will need to add the following lines to your interface:

```

#primary interface
auto eth0
iface eth0 inet dhcp
```

 so that your interfaces should look like:
```
auto lo
iface lo inet loopback

#primary interface
auto eth0
iface eth0 inet dhcp
```

and then run
```
sudo /etc/init.d/networking restart
```

---

### Post by dtoronto on 2010-08-24
installing network manager from the repos is probably the easiest, but you should be able to get online from the steps above

---

### Post by Dyno23 on 2010-08-24
HEYYYYY 

I have updates streaming down!  Nice! I'll wait till updating is done and change this to fixed if all is square.  Mind telling me what happened?  Was it just the removal of network manager?

---

### Post by dtoronto on 2010-08-24
Interface is the file used to assign your ethernet interfaces their IP's.  I believe network manager completely overrides all the info in the interface, and if it was uninstalled it probably left you with an empty interface file.

Glad it is up and working again.

---

### Post by Dyno23 on 2010-08-24
so sweet.  I now have internet.  phase 1 done.  Getting stuff to work has been fun.  The walls I hit are kind of frustrating because I know NOTHING about Linux.  Thanks a ton for the help!

---

### Post by earlf on 2011-09-01
> **dtoronto said:**
> Ok, if your network is set up to administer an IP via DHCP, then you could try.

```
sudo nano /etc/network/interfaces
```

you will need to add the following lines to your interface:

```

#primary interface
auto eth0
iface eth0 inet dhcp
```

 so that your interfaces should look like:
```
auto lo
iface lo inet loopback

#primary interface
auto eth0
iface eth0 inet dhcp
```

and then run
```
sudo /etc/init.d/networking restart
```

thanks dtoronto!

My network connection stopped working and after ambling through cyberspace I came across this post that had your suggestion for the right fix.

---

