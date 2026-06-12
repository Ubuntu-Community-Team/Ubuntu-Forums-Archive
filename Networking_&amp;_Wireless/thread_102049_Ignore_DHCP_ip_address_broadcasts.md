---
title: "Ignore DHCP ip address broadcasts"
date: 2005-12-11
forum: Networking &amp; Wireless
---

### Post by Bodiam on 2005-12-11
Hello all,

I have a small problem with my network configuration. I have configured my pc to have a static ip address, because of some NAT port forwarding. However, my router is a DHCP server, which broadcasts IP addresses. Every 24 hours, my pc gets a new IP address, even though I have configured it to have a static ip address. Does anyone have a suggestion on how to prevent this?

This is my /etc/network/interfaces configuration:
```

 The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
name Ethernet LAN card
address 192.168.1.130
netmask 255.255.255.0
broadcast 192.168.1.255
network 192.168.1.0
gateway 192.168.1.1

```

And this is my /var/log/daemon.log:
```

Dec 11 10:07:28 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Dec 11 10:07:28 localhost dhclient: DHCPACK from 192.168.1.1
Dec 11 10:07:28 localhost dhclient: bound to 192.168.1.6 -- renewal in 35774 seconds.
Dec 11 12:58:52 localhost dhclient: receive_packet failed on eth0: Network is down

```

Thanks for any help!

Erik

---

### Post by ape on 2005-12-11
It looks as though you have dhclient running.  This is what is asking for a lease from your router. The router is doing nothing but responding to your machines requests.    You need to find out what is launching dhclient.  Run `dmsg | grep dhclient` and see if you can see it being initialized at all.

---

### Post by Bodiam on 2005-12-11
Thanks ape, the process was running. I had no idea how to stop it, so I killed it (kill <processid>). After that, it was gone, but in /var/run there were two files left, dhclient.eth0.leases and dhclient.eth0.pid. I renamed the files, and I grepped /etc/ for dhclient, and the only result's I found were these:

```

/etc/dhcp3/dhclient.conf:# Configuration file for /sbin/dhclient, which is included in Debian's
/etc/dhcp3/dhclient.conf:# This is a sample configuration file for dhclient. See dhclient.conf's
/etc/dhcp3/dhclient.conf:#      dhclient.
/etc/dhcp3/dhclient.conf:#script "/etc/dhcp3/dhclient-script";
/etc/dhcp3/dhclient-enter-hooks.d/debug:# are called from /etc/dhcp3/dhclient-script, which exports all the
/etc/dhcp3/dhclient-enter-hooks.d/debug:# /tmp/dhclient-script.debug.
/etc/dhcp3/dhclient-enter-hooks.d/debug:        echo `date`: entering dhclient-enter-hooks.d, dumping variables. \
/etc/dhcp3/dhclient-enter-hooks.d/debug:                >> /tmp/dhclient-script.debug
/etc/dhcp3/dhclient-enter-hooks.d/debug:                echo $i=\'${!i}\' >> /tmp/dhclient-script.debug
/etc/dhcp3/dhclient-enter-hooks.d/debug:        echo '--------------------------' >> /tmp/dhclient-script.debug
/etc/dhcp3/dhclient-exit-hooks.d/debug:# are called from /etc/dhcp3/dhclient-script, which exports all the
/etc/dhcp3/dhclient-exit-hooks.d/debug:# /tmp/dhclient-script.debug.
/etc/dhcp3/dhclient-exit-hooks.d/debug: echo `date`: entering dhclient-exit-hooks.d, dumping variables. \
/etc/dhcp3/dhclient-exit-hooks.d/debug:         >> /tmp/dhclient-script.debug
/etc/dhcp3/dhclient-exit-hooks.d/debug:         echo $i=\'${!i}\' >> /tmp/dhclient-script.debug
/etc/dhcp3/dhclient-exit-hooks.d/debug: echo '--------------------------' >> /tmp/dhclient-script.debug
/etc/dhcp3/dhclient-script:# dhclient-script for Linux. Dan Halbert, March, 1997.
/etc/dhcp3/dhclient-script:        local new_resolv_conf=/etc/resolv.conf.dhclient-new
/etc/dhcp3/dhclient-script:    if ! run_hook /etc/dhcp3/dhclient-exit-hooks; then
/etc/dhcp3/dhclient-script:    if ! run_hookdir /etc/dhcp3/dhclient-exit-hooks.d; then
/etc/dhcp3/dhclient-script:run_hook /etc/dhcp3/dhclient-enter-hooks
/etc/dhcp3/dhclient-script:run_hookdir /etc/dhcp3/dhclient-enter-hooks.d
/etc/dhcp3/dhclient-script:        # receiving an actual address. - dhclient-script(8)

```

Doesn't look like anything is being called here, or did I miss something?

Erik

PS, I don't have 'dmsg', but 'dmesg'. I assume that's what you meant. 
When I run it, it doesn't give any result.

---

### Post by ape on 2005-12-11
Yep, `dmesg` is what I meant.  Still too early to type with any success...<G>

The info you've posted below is just portions of the dhclient config/runtime scripts.  We need to find out how/when this is getting called.  

Is eth0 a standard NIC, or is it a pcmcia card?  Is it wireless?

What does the full contents of your /etc/network/interfaces file look like?  (or did you post the full thing in your earlier post?)

---

### Post by Bodiam on 2005-12-11
> **ape]Yep, `dmesg` is what I meant.  Still too early to type with any success...<G>
[/quote]

early? It's 8pm!  said:**
> 
The info you've posted below is just portions of the dhclient config/runtime scripts.  


Well, actually it was the result of 'find /etc -type f | xargs grep dhclient'..

> 
We need to find out how/when this is getting called.  
Is eth0 a standard NIC, or is it a pcmcia card?  Is it wireless?


Standard, non-wireless nic. Just a simple 100mb card.

> 
What does the full contents of your /etc/network/interfaces file look like?  (or did you post the full thing in your earlier post?)

It's in post one, and the contents have not changed yet, so I don't think it would be very usefull to post it again.

---

### Post by ape on 2005-12-11
I found this older thread that seems exactly like what you are seeing:


[I]Package: gnome-system-tools
Version: 1.0.0-0ubuntu7
Severity: normal
File: /usr/bin/network-admin


I installed Ubuntu from scratch and it automatically set my NIC to get
IP via DHCP. Then I used the GUI tool (one in menu in default desktop
settings, network-admin, I think) to change it from DHCP to static IP.

After this the IP changed to the static one, but every three days it
changed back. /etc/network/interfaces was correct, _but_ dhclient
was still running and it seems it kept changing the address back.
/etc/init.d/networking restart fixed the problem for next three days,
but then it reoccurred. dhclient was visible at the process list.

Thus: I think the network-admin tool should stop/start dhclient
when user changes IP address from dynamic to static or vice versa.

My /etc/network/interfaces:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
name Ethernet lÃ€hiverkkokortti
address 192.168.0.2
netmask 255.255.255.0
broadcast 192.168.0.255
network 192.168.0.0
gateway 192.168.0.1

This process showed up in process list:
dhclient3 -pf /var/run/dhclient.eth1.pid -lf
/var/run/dhclient.eth1.leases eth1[/I]


Is this the same thing that you did?  Have you never rebooted the box since changing the interface to use a static IP, or had you configured it initially to be a static IP address?

---

### Post by Bodiam on 2005-12-11
Wow. This is exactly the same thing as I did. I use it for server purposes only, but to change the DHCP to a static ip address, I thought it would be easier to use the GUI (X) tool. So I did. 

I have never rebooted the machine since (I can do that, to see if dhclient comes up again), and initially I didn't configure anything, so I guess it was using a dynamic address, with a lease time of 24 hours.

---

### Post by ape on 2005-12-12
Cool. I think that probably clears up that mystery...<G>  It is rather strange that switching to static from dhcp via the GUI tools doesn't stop dhclient. I'd file a bug...

---

