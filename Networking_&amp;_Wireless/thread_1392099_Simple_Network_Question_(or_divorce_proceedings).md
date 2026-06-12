---
title: "Simple Network Question (or divorce proceedings)"
date: 2010-01-27
forum: Networking &amp; Wireless
---

### Post by mebunto on 2010-01-27
hello, I'm a linux novice .... I've had terrible problems with a second ethernet connection.  I have a supermicro mb with 2x gigabit (motherboard) connections.  eth0 boots ok and I want eth1 to connect to a separate storage network (drobopro).

/etc/network/interfaces is as follows:
[INDENT][FONT=Verdana]auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# The secondary network interface
iface eth1 inet static
address 192.168.2.81 
netmask 255.255.255.0
auto eth1
[/FONT][/INDENT]on boot, only eth0 starts but if I force a start thus:
sudo ifconfig eth1 192.168.2.81 up
the nic gets the message.

How do I get eth1 to start on boot?

I've spent three days with this and my wife's not impressed

---

### Post by MaindotC on 2010-01-27
> **mebunto said:**
> on boot, only eth0 starts but if I force a start thus:
sudo ifconfig eth1 192.168.2.81 up
the nic gets the message.


I don't understand what this phrase means.  In any event, the only thing I can think of is you may need to define a gateway - a default address to route out all requests.  I used [this tutorial](http://is.gd/7b9Gq) as a guide.

---

### Post by Iowan on 2010-01-27
Hopefully the DHCP address (eth0) is in a different subnet.

---

### Post by mebunto on 2010-01-27
> **strAlan said:**
> I don't understand what this phrase means.  In any event, the only thing I can think of is you may need to define a gateway - a default address to route out all requests.  I used [this tutorial]("http://is.gd/7b9Gq") as a guide.

strAlan OK - I mean that eth1 acquires its ethernet address as set.

eth0 has an address of 192.168.0.10  subnet mask is 255.255.255.0

I have found many postings on this kind of issue but it seems that none of the answers cure my problem.

---

### Post by jimshawnz on 2010-01-27
You don't say what version of Ubuntu you are running. 

I would remove any configuration for the hardware NICs from /etc/network/interfaces and configure them through NetworkManager on the toolbar.

---

### Post by mebunto on 2010-01-27
jimshawnz, thank you.  I'm using Ubuntu Server 9.10 Karmic Koala so network manager isn't supposed to be used and isn't a menu option.

---

### Post by mebunto on 2010-01-28
Can anyone else help? (please!)

---

### Post by dmizer on 2010-01-28
> **mebunto said:**
> jimshawnz, thank you.  I'm using Ubuntu Server 9.10 Karmic Koala so network manager isn't supposed to be used and isn't a menu option.

Have you installed any of the desktop metapackages like ubuntu-desktop, or is your server CLI only?

Also, when you turn on the server, is there an active ethernet connection? I have noticed that adaptors do not want to come up unless they are connected to a switch, or other live connection.

---

### Post by mebunto on 2010-01-28
Dmizer - yes I have installed Ubuntu desktop and also winadmin.  You may have a point about the network connection, my next step will be to configure a switch so that the second network is always connected to something as at the moment it's not connected.
Thanks very much.  I'll post this evening and let you know how I've done.

---

### Post by chili555 on 2010-01-28
> auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# The secondary network interface
iface eth1 inet static
address 192.168.2.81
netmask 255.255.255.0
auto eth1Please try it like this:```
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# The secondary network interface
auto eth1
iface eth1 inet static
address 192.168.2.81
netmask 255.255.255.0
gateway 192.168.2.1
```Thanks.

---

### Post by dmizer on 2010-01-28
> **mebunto said:**
> Dmizer - yes I have installed Ubuntu desktop and also winadmin.  You may have a point about the network connection, my next step will be to configure a switch so that the second network is always connected to something as at the moment it's not connected.
Thanks very much.  I'll post this evening and let you know how I've done.

If you have installed Ubuntu-desktop, then you most likely have network-manager installed. Since that is the case, it's important for you to know that network-manager interferes with traditional Linux networking. If you want networking to work correctly via /etc/network/interfaces, then you'll have to make sure that network-manager-gnome is not installed. Do a search for this package in Synaptic. If it exists, uninstall it and see if that fixes your problem.

Also, if you wanted a GUI, you should have installed a GUI version of Ubuntu, as the server version is tuned to perform well without a GUI.

---

### Post by mebunto on 2010-01-29
Problem solved ..... I'm very happy thank you.
I removed both network manager and network manager gnome, rebooted and now all works as I'd hoped.
I didn't need to change the interfaces file at all, nor did a network connection have to be present.  It was purely the two "manager" programs/suites that caused the issue.
About using Linux Server without the GUI - I'm very new to this so the gui has helped along the way, although it also caused my biggest problem!!  My plan is to get everything that I want to work then rebuild from scratch.  I think I may have enough courage to build the non-gui version at that point.
Thank you all for your contributions, whether they were right or wrong.
How do I mark this as "solved"?

---

### Post by bill1277 on 2010-01-29
Hi,

I am having the exact same problem that this thread was started with.  I am running Ubuntu 8.04 and everytime I restart my computer eth0 fails to come up.

Both eth0 and eth1 are configured for static addresses and are always connected to a switch.  

I use this PC to gain access to a lab environment with a private network that is connected to eth1.  Unfortunately that is the NIC that always comes back up, while I have to manually visit the computer and type sudo ifconfig eth0 IP_ADDRESS to get eth0 to come up.

I took the suggestion and removed **network manager** and **network manager gnome**  but that hasn't fixed the issue.  Is there something else that could be causing this?

Thanks for the help.

/etc/network/interfaces looks like

auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.0.21
netmask 255.255.255.0



iface eth1 inet static
address IP_Address
netmask 255.255.255.0
gateway IP_Address

---

### Post by dmizer on 2010-01-29
> **bill1277 said:**
> 
/etc/network/interfaces looks like

auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.0.21
netmask 255.255.255.0



iface eth1 inet static
address IP_Address
netmask 255.255.255.0
gateway IP_Address

Please show a dump of the _**actual**_ /etc/network/interfaces file without edits. As long as you do not have any external IP addresses listed in your interfaces file, you're not revealing anything sensitive.

---

### Post by bill1277 on 2010-01-29
The lab is a mock up of production so they are actually external ip's they just can't get anywhere, but also exist in our production environment.  Hence the edits.

thanks

---

### Post by dmizer on 2010-01-29
> **bill1277 said:**
> The lab is a mock up of production so they are actually external ip's they just can't get anywhere, but also exist in our production environment.  Hence the edits.

thanks
Put "auto ethX" above each ethernet configuration like so:
```
auto lo
iface lo inet loopback

[COLOR="Red"]auto eth0[/COLOR]
iface eth0 inet static
address 192.168.0.21
netmask 255.255.255.0


[COLOR="Red"]auto eth1[/COLOR]
iface eth1 inet static
address IP_Address
netmask 255.255.255.0
gateway IP_Address
```

> **Objekt said:**
> I have been having a similar problem.  My Ubuntu 9.10 (64 bit regular old desktop version) machine has two NICs, eth0 and eth1.  eth0 does not connect to my router (and thus the Internet) automatically.  I have to manually click on it in the NetworkManager applet after every reboot.

Internet connection sharing has also been impossible.  I gave up trying to do that after about 2 weeks.  I was simply trying to share my Internet connection with a Windows XP machine over eth1, but it never worked.  I could ping one machine from the other, but couldn't get to the Internet from the Win XP machine.

Removing NetworkManager may be the ticket.  Most of the tutorials for Internet connection sharing tell you to enter commands in the console.  Maybe one of them will work once I remove the NetworkManager applet.

Your problem is probably something else entirely. I suggest posting a new thread. Or, you could install gnome-network-admin, uninstall network-manager-gnome, and manage your network from system > administration > network. However, NetworkManager does have some nice tools for ICS, so you should consider this carefully.

---

### Post by bill1277 on 2010-01-29
That looks like it worked.  I was able to restart the machine a couple of times and still access it through the eth0 IP address

Thanks.

---

### Post by mebunto on 2010-02-15
Hello All - you may be interested to know that after two weeks of fiddling and searching, I've finally managed to get to the point where I'm happy.  ISCSI works, drobopro mounts, I have a folder /media/DROBO that has an ext3 partition of 8TiB which I have shared using Samba.  That's more or less where I wanted to be.
It's thanks to forums like this, how-tos on various websites, blogs, and the Drobo support pages.  Hard work is probably not the word but (at my age) here's an old dog that's learned some new tricks!
I plan to do a how-to because I don't want anyone else to go through the heartache that I went through ..... we'll see if the system stays stable over the next few weeks though.  I also plan to buy a [FIT-PC]("http://www.fit-pc.com/web/") and do this from cradle to grave.  That'll give me an always-on linux box with Karmic Koala and a drobopro that will be managed and shared across my home network.
I tried to use ext4 but that was scary biscuits as it threw up a lot of errors - not sure what they were.
[FONT=Century Gothic]Samba sucks (imho, in some ways) because it's very slow but it was easy to get working - what's the alternative?
[/FONT]No coffee was consumed at any time during the proceedings, but PG Tips was!!!  Are there any such things as "ubuntu leaves"??

---

