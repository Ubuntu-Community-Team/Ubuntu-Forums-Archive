---
title: "won't start eth0 on boot, must perform 'ifup eth0' at prompt."
date: 2006-01-02
forum: Networking &amp; Wireless
---

### Post by hodgepodge on 2006-01-02
Hello,

I tried searching the posts for a similar problem, but couldn't find anything.

I'm trying to get Ubuntu 5.10 working on an old Dell PowerEdge 4200.  I didn't have problems with 5.04, but 5.10 won't start the eth0 interface during boot, so it doesn't sync the clock, etc.

Once I get to a prompt, ifup eth0 get's the ip from my dhcp server, and everything works, but I don't understand why it's not starting at boot.  I think it may have something to do with the hotplug system not working on my older computer.  Not sure how to properly fix this.  I assume I must make a change in the /etc/network/interfaces file, but not sure what change to make.

Thank you in advance for you help.

Here's the contents of my interfaces file, minus comments and blank lines:

START /etc/network/interfaces
auto lo
iface lo inet loopback
mapping hotplug
            script grep
            map eth0
iface eth0 inet dhcp
END /etc/network/interfaces

--Steven

---

### Post by Zelut on 2006-01-02
Your interfaces file looks about how it should to me.. let me double-check mine to compare.  Yeah, mine looks exactly the same and I have no problems so I doubt its that file.

Why do you say the hotplug system isn't working?  Do you get an error?  What are the specs on the machine?

---

### Post by hodgepodge on 2006-01-02
It's an old Dell PowerEdge 4200 server I purchased for $50.

It's a dual proc Pentium II 300 system with 512mb RAM, and 2 scsi hd.
I'm using an an Intel 10/100 PCI card.

I'm using LVM for everything but /boot and /

The only error I get on boot relates to not being able to sync the clock with ntp.

When I first log in, the only interface that comes up with ifconfig is lo.

But the e100 driver is loaded.

So:
$ sudo ifconfig eth0 up
adds the interface to ifconfig, but without an IP

then:
$ sudo dhclient eth0

successfully get's an IP address, then I'm good to go.

Is there a method for simply adding the interface directly, without going through the hotplug subsystem?

Thanks for responding.

--Steven

---

### Post by Zelut on 2006-01-02
That does sound odd.. I'm not sure the card I'm using for my eth0 on my old server but I haven't had problems like that.

I suppose you could try making a secondary boot script in /etc/init.d/ to do the sudo ifup eth0 for you...  not sure what else to try.

---

### Post by Lambert on 2006-01-02
add a line and make it look like this.

auto etho
iface eth0 inet dhcp

---

### Post by hodgepodge on 2006-01-02
Thanks, that did the trick.

--Steven

---

### Post by movrshakr on 2007-12-22
> **Lambert said:**
> add a line and make it look like this.

auto etho
iface eth0 inet dhcp

Help a student learn:  "add a line..." to what?

LATER: nevermind...concluded it meant to the interfaces file.  So, no need to answer if that is correct

---

### Post by GabrieisWings on 2008-03-17
I want to do that, And I'm trying, but it won't let me. It says I don't have permission.

How can I not have permission? I'm the only user, and the admin, so...

help me?

---

### Post by Iowan on 2008-03-17
```
sudo nano /etc/network/interfaces
```

---

### Post by movrshakr on 2008-03-17
Or, to use a more wysiwyg editor if you are not familiar with nano...
```
sudo gedit /etc/network/interfaces
```

---

