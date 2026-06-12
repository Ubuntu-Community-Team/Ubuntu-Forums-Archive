---
title: "dhcp server on ubuntu"
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by FableBlaze on 2011-05-06
Hi,

Im really new to linux and i have a homework where i have to set up a dhcp server on linux. I am using ubuntu. I tried following: [http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html ]("http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html")
However after running "sudo apt-get install dhcp3-server" the file "/etc/default/dhcp3-server" does not appear.

---

### Post by poolet on 2011-05-06
doesn't make sense.... 

copy the following code in terminal and paste the output here.... 

**sudo vi /etc/default/dhcp3-server**

---

### Post by Iowan on 2011-05-06
When I upgraded my server a few years ago, I opted for [http://www.thekelleys.org.uk/dnsmasq/doc.html]("http://www.thekelleys.org.uk/dnsmasq/doc.html") It works on my small home network - and ties DNS and DHCP together so I can ping DHCP clients by name. It's in the repos - at least for my version (8.04?)

---

### Post by varunendra on 2011-05-07
> **Iowan said:**
> When I upgraded my server a few years ago, I opted for [http://www.thekelleys.org.uk/dnsmasq/doc.html](http://www.thekelleys.org.uk/dnsmasq/doc.html) It works on my small home network - and ties DNS and DHCP together so I can ping DHCP clients by name. It's in the repos - at least for my version (8.04?)

I can confirm that it (dnsmasq) still exists in the default repositories (Ubuntu 10.10), as well as dhcp3-server. Either can be installed using synaptic GUI.

And the file "/etc/default/dhcp3-server" was created in my case (again, Ubuntu 10.10 on VBox) after (trial) installation of dhcp3-server.

---

### Post by poolet on 2011-05-07
> **varunendra said:**
> I can confirm that it (dnsmasq) still exists in the default repositories (Ubuntu 10.10), as well as dhcp3-server. Either can be installed using synaptic GUI.

And the file "/etc/default/dhcp3-server" was created in my case (again, Ubuntu 10.10 on VBox) after (trial) installation of dhcp3-server.

same situation here. Clear installation at 10.4 and the file  "/etc/default/dhcp3-server" was created.

---

### Post by FableBlaze on 2011-05-07
> **poolet said:**
> doesn't make sense.... 

copy the following code in terminal and paste the output here.... 

**sudo vi /etc/default/dhcp3-server**

Currently i have downloaded and installed ubuntu server 11.04 on a virtual machine in virtualbox.

I have only run commands:
sudo apt-get update
sudo apt-get install dhcp3-server
sudo vi /etc/default/dhcp3-server

The last command opens up a new empty file.



Ok, i think i found it at /etc/default/isc-dhcp-server
I also found dhcpd.conf in /etc/dhcpd/ (should be in /etc/dhcp3/)

Is there a reason why these files appear in different places then in all the tutorials i have found?
Also i'm going to install GUI with "sudo apt-get install ubuntu-desktop"

---

### Post by FableBlaze on 2011-05-07
I have given up on doing this on ubuntu as even the first install does not do what it is supposed to...

Synaptic Package Manager has the following to say about the installed dhcp3-server package
```
This is a dummy package to aid in transitioning from the v3 DCHP packages to the new-style DHCP packages. This dummy package may be safely removed after upgrading to squeeze
```

---

### Post by varunendra on 2011-05-08
> **FableBlaze said:**
> I have given up on doing this on ubuntu as even the first install does not do what it is supposed to...
Sorry to hear that.

But if it's just for a homework, then why don't you use Ubuntu 10.10 where everything is where it is expected to be?

For 11.04, here's an example (I haven't tested 11.04 myself): [http://www.server-world.info/en/note?os=Ubuntu_11.04&p=dhcp](http://www.server-world.info/en/note?os=Ubuntu_11.04&p=dhcp)

At the very top of the above linked page, it is mentioned that >  If you make your linux computer DHCP server, it's neccesarry to disable DHCP function on router in LAN .... have you crosschecked if this is why your installation is failing to do what it's supposed to..?

---

### Post by FableBlaze on 2011-05-08
> **varunendra said:**
> Sorry to hear that.

But if it's just for a homework, then why don't you use Ubuntu 10.10 where everything is where it is expected to be?

At the very top of the above linked page, it is mentioned that  .... have you crosschecked if this is why your installation is failing to do what it's supposed to..?

How would i do that?

Both client and server will be guest machines running on VirtualBox. Server is required to have three network interfaces (nat&#8217;ed network interface, internal network interface connecting client and server, host-only network interface for host nw-access) . Client will have only one network interface (the internal one with server)

I'll also give ubuntu 10.10 a go tomorrow.

EDIT: What about the description saying that this is a dummy package?
Ubuntu server 10.04 LTS should be ok instead 10.10 i think. I'll do clean install in one of the lectures tomorrow and try if it works.
Also, adding GUI to the server shouldn't really change anything? Except makeing it easier for me to work with.

EDIT2: Could it be possible that i have set the network interfaces incorrectly in virtual machine settings?

---

### Post by FableBlaze on 2011-05-08
Ok, i decided to play around with it tonight.

And it seems to work without a problem on Ubuntu server 10.04 LTS. Atleast everything worked as it should. Thank you all for your help, it seems that all i needed was a bit older linux version :D

---

### Post by varunendra on 2011-05-09
> **FableBlaze said:**
> And it seems to work without a problem on Ubuntu server 10.04 LTS. Atleast everything worked as it should.
Hope it goes well from now on.. :)

> **FableBlaze said:**
> EDIT: What about the description saying that this is a dummy package?
....
Also, adding GUI to the server shouldn't really change anything?
I'm sure that synaptic in 10.04 isn't showing it as a dummy package. They might have advanced it to something else in 11.04,.... but 'squeeze'?? I've no idea what's going on.. :)

And yeah, adding GUI 'shouldn't' change anything except additional resource usage (often unnecessary in a server).

---

