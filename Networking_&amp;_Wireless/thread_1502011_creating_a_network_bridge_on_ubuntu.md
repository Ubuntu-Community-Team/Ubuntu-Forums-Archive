---
title: "creating a network bridge on ubuntu"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by sundays211 on 2010-06-05
hi
can anybody help me set up a network bridge between my Internet/network and another computer (both wired), or atleast point me toward an up-to-date guide(all the guides i have found are 5 years old). 
thanks

---

### Post by AHOHA on 2010-06-05
hi 

```
sudo apt-get update
sudo apt-get install bridge-utils

```


and write

```
ifconfig [COLOR=Red]<interface 1>[/COLOR] 0.0.0.0 <<BR>>
ifconfig [COLOR=Blue]<interface 2>[/COLOR] 0.0.0.0 <<BR>>
brctl addbr [COLOR=SeaGreen]<bridge name>[/COLOR] <<BR>>
brctl addif [COLOR=SeaGreen]<bridge name>[/COLOR] [COLOR=Red]<interface 1>[/COLOR] <<BR>>
brctl addif [COLOR=SeaGreen]<bridge name>[/COLOR] [COLOR=Blue]<interface 2>[/COLOR] <<BR>>
ifconfig [COLOR=SeaGreen]<bridge name>[/COLOR] up

```




thanx:)

---

### Post by BoneKracker on 2010-06-05
I hope he/she understands that you didn't mean he/she should type <<BR>> at the end of those commands.

---

### Post by sundays211 on 2010-06-05
although this does work, there is a few problems.
1) when I restart the bridge resets.
2) don't know whether this is possible to fix, but I would like to allow this computer to access the network as well as being a bridge.

---

### Post by ub-newbie on 2010-06-05
Sundays211, 
I'm working on the same problem..  I added ```
iface br0 inet dhcp
bridge_ports all
``` to /etc/network/interfaces (and DON'T comment out any line with "lo").  Then ```
sudo ifup br0
```  It created a bridge, but ping time decreased, so I ```
sudo ethtool -K br0 sg off tx off tso off
``` which helped..  But, I had same problem as you, after restart bridge went away.  I put "/sbin/ifup br0" in /etc/rc.local.  .

To solve the (non)-issue of bridge_utils kicking the error "postconf: fatal: open /etc/postfix/main.cf: No such file or directory" I ```
sudo ln -sf /usr/share/postfix/main.cf.dist /etc/postfix/main.cf
```  But this should not be required..

Also, if you want your bridge to have a static ip, add this (instead of above) to "/etc/network/interfaces": (replace my IP's with yours)
```

iface br0 inet static
	address 192.168.9.XXX
	netmask 255.255.255.0
	gateway 192.168.9.XXX
	bridge_ports all

```

---

### Post by BoneKracker on 2010-06-05
To make it persist after restart, you need to add it to your distro's networking scripts.  I don't use Ubuntu, so I don't know how you would do that.  In a general sense, it's just another startup script.

As to the network latency, forwarding delay might have something to do with that (although I'm not sure).  A bridge interface has something called a "forwarding delay", which you can set to 0 like so:
```
brctl setfd br0 0
```

However, the default forwarding delay is there for a reason, so you should study what this is and how it works before making any changes.  _I emphasize this because I don't really know what it is or how it works, and I don't want to be blamed for your misfortunes._  (I do, however, use it on a bridge that I have, although there is nothing connected to it but virtualized guest operating system instances on the same physical machine as the bridge.)

---

### Post by ub-newbie on 2010-06-10
To have it persistent with Ubuntu 10.4, place ```
/sbin/ifup br0
``` in /etc/rc.local (and make sure it is executable).

---

### Post by snip3r8 on 2010-07-06
> **sundays211 said:**
> although this does work, there is a few problems.
2) don't know whether this is possible to fix, but I would like to allow this computer to access the network as well as being a bridge.

has anybody got an answer to this ?

---

### Post by ub-newbie on 2010-08-14
snip3r8
   I can connect to the Internet on the computer & pass traffic through the bridge (to the webcam) at the same time.

---

