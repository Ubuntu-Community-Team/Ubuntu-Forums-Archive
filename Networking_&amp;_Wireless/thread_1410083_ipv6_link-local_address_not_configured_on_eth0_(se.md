---
title: "ipv6 link-local address not configured on eth0 (server)"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by Skaperen on 2010-02-18
I added an init script numbered just before bind9 starts, which needs to see the ipv6 link-local address on eth0. Sometimes this address is not configured, yet. In all cases it eventually is configured.

I am unable to find any script that is configuring the ipv6 link-local address (which is in part based on the MAC address). Does anyone know if there is some script or program that is supposed to be doing this, or is it an internal kernel function?

One workaround I am considering is making this init script go into a loop around sleep 1 to keep checking for the ipv6 address. But I'm concerned this might cause some problems.  Any suggestions?  I don't want to let it move on to start bind9 until the configuration this script does (more ipv6 addresses) is done.

This is on Ubuntu 9.10 server (for which there is not a prefix choice).

---

### Post by puppywhacker on 2010-02-18
The network is configured either with NetworkManager or by the /etc/network/interfaces file. I think NetworkManager starts up as part of the GUI and the interfaces files is read at startup of /etc/init.d/networking which triggers the ifup scripts which runs the /sbin/ifup program

If you configure the interfaces with the interfaces file you can also trigger an arbitrary command or script with the "up" command in the stanza. I actually misuse the up command to configure the ipv6 addresses, although it could have been done by normal configuration. But a valid "up" statement is the one that triggers ddclient every time the interface is brought up.

```

auto wlan0
iface wlan0 inet dhcp
	wireless-essid zyxel
	up ip -6 addr add fec0::1:2/64 dev wlan0
	up ip -6 addr add 2001:1234:56f::2/48 dev wlan0
	up ddclient
```

I do not fully understand why you want to use a script to find the link-local address since it is always the same regardless if the interface is already up and configured. link-local addresses starts with fe80 and the host part is the OUI-64. Since most mac-addresses are the older OUI-48 format, the FF:FE is pasted in the middle.

so mine is always:
```
inet6 addr: fe80::211:24ff:fea1:79c5/64 Scope:Link
```

Ohh and I use fec0::1:2 as site local ip address since I can remember those. and I have a SIXXS tunnel but I changed my ipv6 addresses for a little bit of privacy.

---

### Post by Skaperen on 2010-02-18
The link-local ipv6 address is already configured, so I should not have to do it myself.  After all the init scripts are run, and I login (via ipv4 if this problem happens), I can do "ifconfig" or "ip addr show" and see that the local-local ipv6 address is configured (but it is not usable to log in to, so when this problem happens I have to use ipv4).

Yes, the address is always the same on the same server with the same NIC card. But it is different on different servers. This is why I am trying to get the link-local ipv6 address in my script ... to get the lower 64 bits from it and form a unique-local address and configure that automatically without having to fiddle with the /etc/network/interfaces file (which doesn't operate cleanly for alias IP addresses, which is the other reason for this script ... to configure all the IP aliases).

As a side note, when I configure a lot of addresses via /etc/network/interfaces, it makes a big mess ... servers keep getting restarted for each address, which also majorly slows the boot time.  By having a script run at a low sequence number, before any network service is started, it can configure all the IP addresses there and then, all at once, without constantly kicking server programs around (which sometimes won't restart, too).  This works fine for statically coded ipv4 and ipv6.

The problem is if the ipv6 link-local address is not available at this time (usually it is, but sometimes, about 10% of the time, it is not), then my script can't generate the unique-local address from it.

Whatever it is that does whatever needs to be done to cause the link-local address to be bound to the interface ... apparently isn't working instantly.  MAYBE a separate process is running to set that up and this is a timing issue.  If this is so, I want to find that and find some way to synchronize this better.  OR MAYBE the kernel has to go through asynchronous steps to set it up, and that's being slow enough sometimes that it can fail to be present when some services are started.

Wherever something is being done, I want to insert an "ifconfig" command at that point to output the interface state to a file and determine if the ipv6 link-local address really is configured when the command exits.  If not, I need to address that somehow.

The link-local ipv6 addresses don't really work.  They may work at a stack and interface level, but they don't work at a socket level ... applications either can't get a socket bound, or don't even try (apparently because they detect that it is a link-local address).  Once configured, the unique-local addresses work within my LAN.

FYI I generated a random ULA address in fd00::/8 and registered it at the SIXXS ULA registration page. I'm not using any tunnels for global access at this time.  It is that address, with subnet 0000, that I am appending the lower 64 bits from the link local address to.

If you want to see the scripts, I can provide those.

---

### Post by Skaperen on 2010-02-18
> **puppywhacker said:**
> link-local addresses starts with fe80 and the host part is the OUI-64. Since most mac-addresses are the older OUI-48 format, the FF:FE is pasted in the middle.My understanding is that the link-local is EUI-64 which also involves a bit being changed in part of the address when derived from from the 48 bit MAC address (not sure why, but that was I read at an IEEE page referenced from Wikipedia). The link local addresses I do get are consistent with that.  Because of that one bit, it became non-trivial to form the ULA address in a script.  The easiest way to get it was to extract it from the LL address. That's what I coded my script to do and that is what sometimes fails because sometimes the LL address is not (configured, ready, available, visible ... take your pick).

---

### Post by puppywhacker on 2010-02-18
my bad, the OUI is the organizational part ... the first 3 bytes indicating the manufacturer. The EUI is the whole address.

please post the script, I'm interested in all different ways to solve issues. I do not share your experiences on flaky aliasses for interfaces but then again, millage varies. I also have a limited amount of systems to worry about so hand configuring is not a big issue for me :)

---

### Post by Skaperen on 2010-02-18
I put the scripts in this directory:  [http://phil.ipal.org/ubuntu/files](http://phil.ipal.org/ubuntu/files)

with names translated by changing slash to underscore (but existing underscores retained).  In case there are troubles accessing files with no extensions, they are also linked with names ending in ".txt" (so you will see 2 copies of each file in the directory listing).  The script that goes in "/etc/init.d" is a small one that runs the larger one I put in "/etc/network".

---

### Post by sakumarit on 2010-07-22
> **Skaperen said:**
> I put the scripts in this directory:  [http://phil.ipal.org/ubuntu/files](http://phil.ipal.org/ubuntu/files)

with names translated by changing slash to underscore (but existing underscores retained).  In case there are troubles accessing files with no extensions, they are also linked with names ending in ".txt" (so you will see 2 copies of each file in the directory listing).  The script that goes in "/etc/init.d" is a small one that runs the larger one I put in "/etc/network".


I am having the same problem as well.. can anyone help me in this..!!
where is the kernel code present, to generate the link-local address?
I want to know which is the exact place that is generating the link-local address..

   [FONT=&quot][/FONT]

---

