---
title: "Filesharing via crossover cable"
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by mpm on 2009-08-02
I'm trying two connect two ubuntu 9.04 boxes (desktop/laptop) via a crossover cable.  I've pulled it off with the same two boxes under 8.10 (on both), but I don't remember how.  I've created a samba share on the desktop that I can connect to from a virtual machine on the same box (via the wireless card).
I can connect to same share from the laptop by using Places -> Computer -> and changing the Location to the IP of the wireless card of the desktop, but it never asks for authentication (perhaps because the two systems have the same username).

Yet, I cannot get any connection to work via the crossover cable.  
I think I'm missing something in the configuration of the wired connection (IPv4 settings maybe?).
  
I tried setting the IPv4 settings to 'shared to other computers', but it seems to assign the same IP on both machines.

I've spent a few days racking my brains, but I'm lost. Any ideas?
Thanks!

---

### Post by Iowan on 2009-08-02
What IP addresses are you using for the crossover-connected machines? (Check via **ifconfig -a** in a terminal on each machine.)

---

### Post by mpm on 2009-08-02
Iowan,
This is part of my problem, as it depends on the Ipv4 settings I use.  I think I used DHCP before, but when I use it in 9.04 the machines don't even connect to each other.  

If I use 'Local-link only' the desktop is assigned to 169.254.7.72 and the lap at 169.254.10.69, and I've tried a dozen ways of connecting with these, different, IPs to no avail.  In fact, I can't even ping the IP of the other machine (listed as the IP in ifconfig for device eth0).  

If I set IPv4 to 'Shared with other computers' it assigns the same IP on both machines of 10.42.43.1.  If I connect to this IP with these settings, it only opens the shares on the local machine.  I can ping, but I assume that I'm pinging the same machine.

Thank you

---

### Post by LinuxRules1 on 2009-08-02
Try setting the second system with this static IP. 
```

10.42.43.2

```

---

### Post by lswb on 2009-08-02
Have you ever configured any firewall on either of the systems? If so make sure to open the appropriate ports for whatever you decide to use for file sharing. Most versions of linux from the last few years have working zero-config networking that you mentioned and will automatically assign ip addresses in the 169.254.x.x range. The machines will also be accessible by by name with a tld name of .local, i.e. hostname.local. Make sure all your systems have unique host names and are not using the installed default of "ubuntu" 

IME it is hard to beat ssh for simple file sharing between linux/unix machines. Just install the openssh-server package on one or both systems. The sshfs packages is also recommended. After the server is installed and running on machine A, from machine B you can just select Main Menu/Places/Connect to Server, choose ssh as the type, fill in the fields and follow the prompts. 

The sshfs packages gives you cli tools to mount a remote system (or a directory of a remote system) and have it appear as a local directory, similar to how the mount command works.

---

### Post by mpm on 2009-08-02
I changed the IP on the lap via 'ifconfig eth0 10.42.43.2' then went to Network Go To:smb://10.42.43.1. I Even tried it the other way around. No luck.  I get:
Error: Failed to retrieve share list from server
Please select another viewer and try again.
Seems I can't ping either.

---

### Post by mpm on 2009-08-02
lswb,
I have a firewall running but I'm keeping close tabs on it.  Seeing a blocked connection would make me quite happy.
I tried ssh also with gFTP but am not sure about how to set the IPv4 settings, as the assigned IPs change.  I can get gFTP to connect to the same machine (when it assigns the same IP to both machines) quite easily and transfer files.  I can also use it with a wireless connection, but I can't get it to recognize the ethernet device.

---

### Post by LinuxRules1 on 2009-08-02
You might have to make the whole connection static. Try editing your /etc/network/interfaces file to look like this

The main system
```

auto (network card)
iface (network card) inet static
     address 173.16.0.1
     netmask 255.255.255.0

```

The other system
```

auto (network card)
iface (network card) inet static
     address 173.16.0.2
     netmask 255.255.255.0

```

Hope this works for you.

---

### Post by mpm on 2009-08-02
LinuxRules1,
Sorry for being a noob, but what do you mean by (network card)?
lspci lists:
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
and,
00:08.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01) (this is the wireless card right?)
what part of this should I use?
I tried it using 'eth0' for (network card) but this did not change the output of ifconfig

---

### Post by lswb on 2009-08-02
I have no way to test at the moment, but a few things occur to me. You mention a wireless network, make sure that any wireless adapters are shut off or wireless networking disabled when using the crossover cable. IIRC NetworkManager dislikes more than one interface. BTW, make sure that it really is a crossover cable!

If I was going to troubleshoot this on my own systems, the 1st thing I would do is restore /etc/network/interfaces to OEM, i.e. the only contents would be
```

auto lo
iface lo inet loopback

```

If there are no Windows boxes to be concerned with forget about samba for now and just try to get the machines to ping each other successfully, then try ssh or ftp or some other reliable linux/unix service.

My preference would be to let avahi/zero-config do its thing and use the self-assigned 169.254.x.x addresses unless you have some reason to do otherwise. If I couldn't ping using the 169.254.x.x addresses within a moment or 2 of plugging in the crossover cable, I'd try shutting down Network Manager and trying again. In 9.04 the command is "sudo /etc/init.d/NetworkManager stop" and to restart it just change "stop" to "start"

---

### Post by mpm on 2009-08-02
lswb,
THANK YOU!!!  As it turns out I acutally knew what I was doing (which is quite rare). All I had to do was disable the wireless devices and it worked perfectly.  Now if I could only mark this as 'solved'...

---

### Post by pastorelli on 2009-08-26
I have the very same problem in the very same cards... actually not very same problem because im trying to make it via samba...
i can make machines ping each other but that is all... some time ago i made the network works, but after a few days without using it it simply crashed... mabe some update issue... im still working on it... ill update if i find something

---

