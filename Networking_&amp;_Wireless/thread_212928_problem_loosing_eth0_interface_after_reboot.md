---
title: "problem: loosing eth0 interface after reboot"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by driesel on 2006-07-10
Hi,

My Ubuntu 6.06 system is running really great now.

But I have one small problem.
Whenever I reboot my PC, the network interface (eth0 wired network to router) is disconnected (sometimes not).
Doing System => Administration => Networking and then deactivating and activating eth0 again (DHCP) solves the problem.
Personally, I can live with this. But the problem is I'm not the only person using the PC.

I feel the has to be a way to permanently have the network interface up and running properly, but I can't figure out how.

Does anyoneknow what I've misconfigured? Should I use a static local IP instead of DHCP?



greetings,
driesel

Kindly awaiting your professional response ;).

---

### Post by Henrythewound on 2006-07-11
I would like to know how to do this as well (bump). My DSL connection has many issues, this being one of them. Im sure there is a file I can edit which will tell ubuntu to activate the DSL connection on startuo (mine is eth0).

Hope some expert stops by,

Joe aka Wound

---

### Post by driesel on 2006-07-11
Yeah,

Something must have been misconfigured, but I'm not really that much into networking.

Hasn't anyone ever got the same problem.  There MUST be a way to solve this, since reactivating manually is quite simple.

Otherwise:

Although I do prefer a more 'clean' solution,
How can I make a script that automatically reactivates the eth0 interface on boot up?


greetings,
driesel

---

### Post by haaglin on 2006-07-11
post your /etc/network/interfaces file..

---

### Post by driesel on 2006-07-11
This is the content of the /etc/network/interfaces file



# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

---

### Post by haaglin on 2006-07-11
try this, worked for me when i had the problem.:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0
iface lo inet loopback

# The primary network interface
iface eth0 inet dhcp

---

### Post by bforbes on 2006-07-11
You could run the script for runlevels 2,3,4,5 and S.
```

su
echo "ifdown eth0;ifup eth0" > /etc/init.d/rebooteth0
update-rc.d rebooteth0 start 2 3 4 5 S .

```

That might work.

---

### Post by driesel on 2006-07-11
Thank you very much :).

I'll give it a try.


greetings,
driesel

---

### Post by driesel on 2006-07-11
I'm sorry, haaglin, but your settings didn't work.
Actually it made the situation a bit worse :).

While initially the symptom occured somewhat randomly, with your settings the network is disconnected every time I reboot.

---

### Post by haaglin on 2006-07-11
ok, sorry #-o . I'll post my file as soon as get home, unless you find a solution before i get home.

---

### Post by driesel on 2006-07-11
> **bforbes said:**
> You could run the script for runlevels 2,3,4,5 and S.
```

su
echo "ifdown eth0;ifup eth0" > /etc/init.d/rebooteth0
update-rc.d rebooteth0 start 2 3 4 5 S .

```

That might work.

I'm sorry, but I'm quite new to Ubuntu and linux in general.

When I put your code in a terminal I get:


```
driesel@driesel-desktop:~$ sudo echo "ifdown eth0;ifup eth0" > /etc/init.d/reboo teth0
bash: /etc/init.d/rebooteth0: Toegang geweigerd
driesel@driesel-desktop:~$
```

'Toegang geweigerd' is Dutch for 'Access denied'.
Also there is no rebooteth0 file in /etc/init.d.  Has this something to do with it?

---

### Post by bforbes on 2006-07-11
You can't use sudo in this case. What happens is, the password prompt for sudo gets redirected to /etc/init.d/rebooteth0, before you have permission to do it. You need to use su, to log in as root first, then do everything.

EDIT: rebooteth0 definately should NOT exist.

---

### Post by plexi50 on 2006-07-11
I am having the same problem, with my wireless eth1. When I first boot, network manager shows connected, but no DNS/web pages. I just deactivate/activate eth1 in System/Admin/Networking, and it works everytime. BTW, this just started happening. It used to work fine everytime, so I am not sure what changed. Other computers, both Linux and Win connect fine to the same router without tweaking.

SOLUTION: check your /etc/networks/interfaces. Somehow, my eth1 was not on auto. Be sure your lines read auto eth1 inet dhcp. Mine works fine now

---

### Post by driesel on 2006-07-12
These /etc/network/interfaces settings did the trick for me:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.2.5
netmask 255.255.255.0
gateway 192.168.2.1


It seems that especially the hotplug part is helping a lot.
Also I changed to static local IP.


greetings,
driesel

---

