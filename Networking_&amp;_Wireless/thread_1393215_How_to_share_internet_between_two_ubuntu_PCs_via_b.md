---
title: "How to share internet between two ubuntu PCs via bluetooth?"
date: 2010-01-29
forum: Networking &amp; Wireless
---

### Post by ario on 2010-01-29
Hi
I have a Desktop and a Laptop. Their Configuration is as below:
Desktop:
[INDENT]OS: Ubuntu 9.04
Bluetooth dangle: YES
Internet Connection: Via LAN (eth0) with a DSL modem[/INDENT]

Laptop:
[INDENT]OS: Ubuntu 9.10
Bluetooth dangle: YES
Internet Connection: **I want to use my desktop internet connection via blutetooth for this computer.**[/INDENT]

So the question is that how to share internet connection between these two Ubuntu computers via **Bluetooth**?
Remember that:
[INDENT]***** I can handle bash.
***** I can send files via bluetooth to two of my PC's. so they're connected.
***** I've seem that big text file over internet ([http://bluez.sourceforge.net/contrib/HOWTO-PAN](http://bluez.sourceforge.net/contrib/HOWTO-PAN)) about using PAND but it wants a file named: /etc/bluetooth/hcid.conf which is not exists on Ubuntu versions later than 8.04. So that this how to is old and useless for me.
***** I've seem that HOWTO about connecting ubuntu PC to internet via mobile phone. I don't mean that!
[/INDENT]
Please help me in the way of ISC between to Ubuntu PC's so that people can enjoy using internet without a Wireless lan dangle and we can make a good how-to here together. 
Thanks for your attention ladies and gentlemen (If any lady here uses Ubuntu instead of windows:D).

---

### Post by ario on 2010-01-29
I used this command:
```
sudo pand --listen -c 00:...MY_LAPTOP_ADDRESS...:10 --role=NAP -n --persist
```
to connect to my laptop using **pand** command. It pops up an Authorization prompt window in my laptop and I checked the "Always grant" option and clicked on "Grant" button.
Whenever the --role parameter is equal to PANU it can connect. But with NAP or GN option it prompts:
```
sudo pand --listen -c 00:15:83:15:A3:10 --role=NAP -n --persist
pand[25545]: Bluetooth PAN daemon version 4.32
pand[25545]: Connecting to 00:15:83:15:A3:10
pand[25545]: Connect to 00:15:83:15:A3:10 failed. Protocol error(71)

```
What is this protocol error (71)? How can I solve it?
Again thanks for your attention people.:)

---

### Post by ario on 2010-01-29
Also tried this one:
[http://www.howtoforge.com/bluetooth_pand_debian_etch](http://www.howtoforge.com/bluetooth_pand_debian_etch)
no sucess!
after using this command:
```
pand --listen -c 00:15:83:15:A3:10 --role=NAP -n --persist
```
it will return just this:
```
pand[10436]: Connecting to 00:15:83:15:A3:10
pand[10436]: Connect to 00:15:83:15:A3:10 failed. Connection refused(111)

```

---

### Post by ario on 2010-01-29
No success with Blueman too. It shows me "Connection Failed: Device already connected".
Any Idea?

---

### Post by ario on 2010-02-02
BUMP!
Here's my terminal:
```
ario@ario-desktop:~$ sudo bash
[sudo] password for ario: 
root@ario-desktop:~# hcitool scan
Scanning ...
	00:24:EF:8B:ED:F2	Ario
root@ario-desktop:~# geany /etc/default/bluetooth
root@ario-desktop:~# apt-get install bluez-compat
Reading package lists... Done
Building dependency tree       
Reading state information... Done
...
..
.
.(some lines here from apt-get)
Processing triggers for man-db ...
Setting up bluez-compat (4.32-0ubuntu4.1) ...
root@ario-desktop:~# pand --connect 00:24:EF:8B:ED:F2
root@ario-desktop:~# pand -K
root@ario-desktop:~# pand --listen --role NAP
root@ario-desktop:~# geany /etc/bluetooth/hcid.conf
root@ario-desktop:~# geany /etc/default/bluetooth
root@ario-desktop:~# geany /etc/default/bluetooth
root@ario-desktop:~# sudo modprobe bnep
root@ario-desktop:~# hcitool scan
Scanning ...
	00:15:83:15:A3:10	
root@ario-desktop:~# sudo pand --listen -c 00:15:83:15:A3:10 --role=NAP -n --persist
pand[15030]: Bluetooth PAN daemon version 4.32
pand[15030]: Connecting to 00:15:83:15:A3:10
pand[15030]: Connect to 00:15:83:15:A3:10 failed. Connection refused(111)
pand[15030]: Connecting to 00:15:83:15:A3:10
pand[15030]: Connect to 00:15:83:15:A3:10 failed. Connection refused(111)
pand[15030]: Connecting to 00:15:83:15:A3:10
pand[15030]: Connect to 00:15:83:15:A3:10 failed. Protocol error(71)
pand[15030]: Connecting to 00:15:83:15:A3:10
pand[15030]: Connect to 00:15:83:15:A3:10 failed. Protocol error(71)
pand[15030]: Connecting to 00:15:83:15:A3:10
```

---

### Post by webdebbyjoss on 2010-03-21
Hi, 

Were you able to resolve this issue?

I'm trying to share internet access from my Windows 7 desktop to Ubuntu based laptop over bluetooth and have the same issue I've found in this thread.

---

### Post by ario on 2010-03-31
> **webdebbyjoss said:**
> Hi, 

Were you able to resolve this issue?

I'm trying to share internet access from my Windows 7 desktop to Ubuntu based laptop over bluetooth and have the same issue I've found in this thread.

Sorry. I didn't not solve this problem and no one answered me in any topic.
Maybe it's impossible to share internet via bluetooth between Ubuntu and something.
"PAND" (The software in "bluez-utils" project that is in charge of connecting via bluetooth), looks like a dead project and seems that no one have the time to update it and solve it's bugs.
Sorry for Open source community. It could be a very exciting ability for linux but it's not working anymore:(.

---

### Post by arkashkin on 2010-04-09
I want to know about this subject too, I wish somebody would answer this post.

---

### Post by ario on 2010-04-11
Still don't know how! Anyone else?

---

### Post by Robespierre. on 2010-05-07
I'm very interested too.

---

### Post by gjmitch on 2010-05-25
> **ario said:**
> I used this command:
```
sudo pand --listen -c 00:...MY_LAPTOP_ADDRESS...:10 --role=NAP -n --persist
```
to connect to my laptop using **pand** command. It pops up an Authorization prompt window in my laptop and I checked the "Always grant" option and clicked on "Grant" button.
Whenever the --role parameter is equal to PANU it can connect. But with NAP or GN option it prompts:
```
sudo pand --listen -c 00:15:83:15:A3:10 --role=NAP -n --persist
pand[25545]: Bluetooth PAN daemon version 4.32
pand[25545]: Connecting to 00:15:83:15:A3:10
pand[25545]: Connect to 00:15:83:15:A3:10 failed. Protocol error(71)

```
What is this protocol error (71)? How can I solve it?
Again thanks for your attention people.:)

I don't know what error 71 means sorry, but did you try pand without the "--persist" switch?  I'm not going to attempt to write a complete HOW-TO right now, but hopefully the following is at least marginally useful, and we can get on the same page. 

On the server side I just use:

```

 pand --listen --role=NAP

```

And on the client-side
```

pand --connect server-mac-address

```

That's worked for me to connect two computers for a long time now.  I have used several approaches to share the server's connection including iptables, bridge-utils, ipmasq/dnsmasq/dhcp3-server and manually routing with the "route" command and all approaches have worked (eventually after some hours of patient fumbling around.)   

I'll say this about the big text file you referenced: ([http://bluez.sourceforge.net/contrib/HOWTO-PAN](http://bluez.sourceforge.net/contrib/HOWTO-PAN))  It helps to go through it over and over again; even though it's outdated (hcid.conf is no longer used) there's still a lot to learn from it. 

What led me to this thread is that I'm struggling to get a third (non GNU) machine connected to my NAP.  

The first two machines connect across bnep0, but the third (androidOS) also wants to connect to bnep0, except that the NAP expects bnep1, and android doesn't have "ifconfig" built into it, so I can't assign the interface an IP from the commandline in android as described in the NAP scenario of [http://bluez.sourceforge.net/contrib/HOWTO-PAN](http://bluez.sourceforge.net/contrib/HOWTO-PAN)
(might edit more into this problem since I've been trying multiple approaches, but I guess that's a little off topic since you're struggling with the first two connections.)

Anyways, hope that helps as a start.



> **ario said:**
> 
Maybe it's impossible to share internet via bluetooth between Ubuntu and something.



It's not impossible, I've been doing it for awhile.  It IS unnecessarily complicated however, I'll agree. 

> **ario said:**
> 
"PAND" (The software in "bluez-utils" project that is in charge of connecting via bluetooth), looks like a dead project and seems that no one have the time to update it and solve it's bugs.
Sorry for Open source community. It could be a very exciting ability for linux but it's not working anymore:(.


The development mailing list is pretty active [http://marc.info/?l=linux-bluetooth](http://marc.info/?l=linux-bluetooth)

What happened to the user mailing list though?  And the maintainer's blog is now empty. [http://www.holtmann.org/linux/bluetooth/](http://www.holtmann.org/linux/bluetooth/)

On the plus side, they just released a new version of the kernel stuff yesterday. [http://www.bluez.org/bluez-465/](http://www.bluez.org/bluez-465/)

Maybe development is moving too fast for them to update us?

---

