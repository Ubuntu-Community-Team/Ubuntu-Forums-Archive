---
title: "[SOLVED] Wired Network No Longer Working :-("
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by Naipes on 2008-12-15
I ***was*** using Ubuntu 8.04 as a file / print share device on my Windows network.

Everything ran great.  No problems for almost a year, until today.

The power went out at my house.  

Now, when Ubuntu reboots it no longer connects to the internet.

I am getting frustrated.  I suspect a file may be corrupted, but I do not know where to look.  I need to get some files off the linux box.  This is an old computer and it does not have a CD Burner.  I need to connect to the internet.

I redid my /etc/network/interfaces file for a static ip address.
It looked like this:

[I]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.2.5
netmask 255.255.255.0
gateway 192.168.2.1
[/I]

But that didn't work.

When the linux box worked, the network was configured to "Enable Roaming Mode" and this always worked fine.  Now it's screwed up big time and I can't figure it out.  I tried a static ip, I tried DHCP and I tried to put "Enable Roaming Mode" back on... nothing works.

Any ideas? Unfortunately, I cannot paste the output of commands into the forum because I cannot connect to the linux box.  I can type in the relevant bits, but I don't want to type verbatim all the crap that comes out of ifconfig.

Are there any Ubuntu Network Gurus out there that can point me in the right direction? 

Thanks

---

### Post by spy_1134 on 2008-12-15
I got frustrated with GNOME's network manager so I switched to Wicd

I haven't had any problems since and it automatically connects wireless as well

---

### Post by Iowan on 2008-12-15
To what does the box connect - router, modem,...? Is it possible that that box got corrupted (reset to default, etc)? Can you ping the gateway device?

---

### Post by Naipes on 2008-12-15
The box connects to a router.  

When the box is set to "Roaming Mode Enabled" and I ping the router I get:

"connect: Network is unreachable"

---

### Post by nolewatcher on 2008-12-15
What router do you use? I have had the same problem with a linksys router, it works fine with Winduhs when I config the adapter STATIC, but I have not had any luck getting either 8.04 or 8.10 to work. Wondered if you are using a Linksys.....

---

### Post by Naipes on 2008-12-15
It's a Netgear.

The thing is, this worked PERFECTLY for MONTHS.  The box was always on and it was on when the power went out.  That's why I wonder if a file got corrupted, but I don't know where to look.

---

### Post by Naipes on 2008-12-16
Does anyone know why eth0 is being deactivated or what is going on here?
(see logs below)

I scanned the results of ifconfig and this is what I got:

ifconfig
eth0 	Link encap:Ethernet Hwaddr OO:eO:29:88:90:55
	UP BROADCAST MULTICAST MTU:15OO Metric:1
	RX packets:0 erx0ts:0 dr0pped:0 0verruns:0 frame:0
	TX packets:O err0rs:O dr0pped:O 0verruns:O caxrie1:0
	collisions:0 txqueue1en:1000
	RX bytes:0 (0.0 B) TX bytes:0 (0-0 B)
	Incerxupt:3 Base addxess:OxecOO

lo 	Link encap:L0cal Lccpback
	inet addr:127.0.0.1 Mask:255.0.0.0
	1net6 addr: ::1/128 Sc0pe:H0st
	UP LODPBACK RUNNING MTU:16436 Metric:}
	RX packets:1272 exx0rs:O dx0pped:O 0ve1runs:O frame:O
	TX packets:1272 exx0xs:O dx0pped:O 0verxuns:O caxrier:O
	c011isi0ns:0 txqueuelen:0
	RX bytes:ll0l20 (107.5 KB) TX bytes:1l0l20 (107.5 KB)

I also scanned sections of my log files:


**Daemon.1og**
Dec 15 23:47:55 UbuntuBox Netw0rkManager: <info> /etc/network/interface changed: rebuilding the device list.
Dec 15 23:47:55 UbuntuBox Netw0rkManager: <info> Removing wired Ethernet (802.3) device 'eth0'.
Dec 15 23:47:55 UbuntuBox Netw0rkManager: <info> Deactivating device eth0.
Dec 15 23:47:55 UbuntuBox Netw0rkManager: <info> Recreating the device list.
Dec 15 23:47:55 UbuntuBox Netw0rkManager: <info> eth0: Device is fully-supported using driver '8139too'.
Dec 15 23:47:55 UbuntuBox Netw0rkManager: <info> nm_device_init(): waiting for device's worker thread to start
Dec 15 23:47:55 UbuntuBox Netw0rkManager: <info> nm_device_init(): device's worker thread started,continuing.
Dec 15 23:47:55 UbuntuBox Netw0rkManager: <info> Now managing wired Ethernet (802.3) device 'eth0'.
Dec 15 23:47:55 UbuntuBox Netw0rkManager: <info> Deactivating device eth0.
Dec 15 23:47:55 UbuntuBox Netw0rkManager: <info> Device list recreated successfully.

**kern.log**
Dec 15 23:47:55 UbuntuBox kernel: [13920.28594l] eth0: link down
Dec 15 23:47:55 UbuntuBox kernel: [l3920.286730] ADDRCONF(NETDEV;UP): eth0: link is not ready

**messages**
Dec 15 23:47:55 UbuntuBox kernel: [13920.285941] eth0: link down
Dec 15 23:47:55 UbuntuBox kernel: [13920.286730] ADDRCONF(NETDEV_UP): eth0: link is not ready

**syslog**
Dec 15 23:47:55 UbuntuBox Netw0rkManager: <info> /etc/network/interface changed: rebuilding the device list.
Dec 15 23:47:55 UbuntuBox Netw0rkManager: <info> Removing wired Ethernet (802.3) device 'eth0'.
Dec 15 23:47:55 UbuntuBox Netw0rkManager: <info> Deactivating device eth0.
Dec 15 23:47:55 UbuntuBox Netw0rkManager: <info> Recreating the device list.
Dec 15 23:47:55 UbuntuBox kernel: [l3920.28594l] eth0: link down
Dec 15 23:47:55 UbuntuBox kernel: [13920.286730] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 15 23:47:55 UbuntuBox Netw0rkManager: <info> eth0: Device is fully-supported using driver '8139too'.
Dec 15 23:47:55 UbuntuBox Netw0rkManager: <info> nm_device_init(): waiting for device's worker thread to start
Dec 15 23:47:55 UbuntuBox Netw0rkManager: <info> nm_device_init(): device's worker thread started, continuing.
Dec 15 23:47:55 UbuntuBox Netw0rkManager: <info> Now managing wired Ethernet (802.3) device 'ethO'.
Dec 15 23:47:55 UbuntuBox Netw0rkManager: <info> Deactivating device eth0.
Dec 15 23:47:55 UbuntuBox Netw0rkManager: <info> Device list recreated successfully.

---

### Post by Naipes on 2008-12-16
Little bump.

Does anyone know why eth0 is being deactivated?  See my log in the post above this one.

If I install 8.10 over my current 8.04 installation will 8.10 overwrite all my current settings?  Would an 8.10 installation fix my internet connection problem?  Can I run 8.10 from the disc without damaging my current installation?

I tried ver 8.10 from the disk and still no connection :-( 

weird... I wonder what is wrong.  I'm going to try the disconnect box from power trick next and see what happens...

---

### Post by Naipes on 2008-12-23
Turns out my SMC Ethernet card was toast.

I bought a new Trendnet card from Newegg.com for $10.99 with free shipping and it works great!  

Back online with Ubuntu.  Figures, it had to do with my hardware being broken and nothing to do with Ubuntu.

---

