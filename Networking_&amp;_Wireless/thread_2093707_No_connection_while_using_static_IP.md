---
title: "No connection while using static IP"
date: 2012-12-11
forum: Networking &amp; Wireless
---

### Post by berndtsson on 2012-12-11
Hey guys, I've been trying to set up some server applications on my desktop computer.

So I started out by setting up a static IP on my wired network. Everything works fine.
I redirect traffic through my router.
Installed openssh on it and tried it out using another computer on another network. 
Everything still works fine.
I tried installing a VPN but couldn't understand what I was doing, so I reverted all settings I had changed and quit. At this point, everything is still working fine.
Later I tried installing apache2, and I noticed I couldn't reach the webpage from outside of my router. I tried connecting to the SSH again. No signal.
This is where I decided to try and restart my computer only to log in and see I have no connection and a string saying **(device not handled)** underneath.

I didn't understand what was going on so I googled on my other computer and found that it might be the static IP that was messing up my connection. I removed it and everything works again.

So I have been trying to adapt methods I found on forums and such, but to no avail. My last attempt at setting up a static IP made my /etc/network/interfaces look like this

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.13
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
	# dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.1.1 #I tried with and without these two lines
        dns-search lcl
```

This looks perfectly in order to me. I have no clue what is causing it not to connect.

Any ideas?

---

### Post by Cheesemill on 2012-12-11
> **berndtsson said:**
> Hey guys, I've been trying to set up some server applications on my desktop computer.

So I started out by setting up a static IP on my wired network. Everything works fine.
I redirect traffic through my router.
Installed openssh on it and tried it out using another computer on another network. 
Everything still works fine.
I tried installing a VPN but couldn't understand what I was doing, so I reverted all settings I had changed and quit. At this point, everything is still working fine.
Later I tried installing apache2, and I noticed I couldn't reach the webpage from outside of my router. I tried connecting to the SSH again. No signal.
This is where I decided to try and restart my computer only to log in and see I have no connection and a string saying **(device not handled)** underneath.

I didn't understand what was going on so I googled on my other computer and found that it might be the static IP that was messing up my connection. I removed it and everything works again.

So I have been trying to adapt methods I found on forums and such, but to no avail. My last attempt at setting up a static IP made my /etc/network/interfaces look like this

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.13
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
    # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.1.1 #I tried with and without these two lines
        dns-search lcl
```This looks perfectly in order to me. I have no clue what is causing it not to connect.

Any ideas?
Surely your entry for dns-nameservers should either be the IP of an external DNS server or your router. Try using the line:
```
   dns-nameservers 192.168.0.1
```

---

### Post by ahallubuntu on 2012-12-11
If by chance you have control over the router and have the ability to make DHCP reservations (almost all routers can do this), avoid the hassle of the static IP entirely and just fix the IP in the router with the reservation.  (It's based on the MAC address of the network card connected to your router.)  That way, you can leave the Ubuntu box set to automatic/DHCP but it will always get the same IP according to your router.

---

### Post by dannyboy79 on 2012-12-11
> **Cheesemill said:**
> Surely your entry for dns-nameservers should either be the IP of an external DNS server or your router. Try using the line:
```
   dns-nameservers 192.168.0.1
```
+1

but I always set dns-nameservers 8.8.8.8 8.8.4.4 in my interfaces file but that's just me.

---

### Post by berndtsson on 2012-12-12
> **ahallubuntu said:**
> If by chance you have control over the router and have the ability to make DHCP reservations (almost all routers can do this), avoid the hassle of the static IP entirely and just fix the IP in the router with the reservation.  (It's based on the MAC address of the network card connected to your router.)  That way, you can leave the Ubuntu box set to automatic/DHCP but it will always get the same IP according to your router.

I commented away all the static stuff in /etc/network/interfaces and gave the computer a static DHCP address, and also put it in DMZ so that traffic on all ports can reach this computer.
That worked fine and I now have a static IP on this computer BUT I can't reach it from outside the router. I can ping my own IP but I can't connect to the SSH service on the computer except from using ```
ssh localhost
```

I could list all the files I think might have to do with this issue, but I have reverted all possible settings I have changed in them..

By now I am considering just re-installing Ubuntu all in all, I don't really have any important data on this computer anyways.

---

### Post by dannyboy79 on 2012-12-12
did you set your sshd_config to listen on something other then 127.0.0.1 so you can connect to it from outside your lan? if it's in a DMZ you shouldn't have to port forward any ports. this is a dangerous pratice however, I wouldn't put a computer into a DMZ unless you're entirely certain you're fully aware of all security vulnerabilites and running services within your ubuntu machine. i would merely forward only port 22 to the static IP you set for the ubuntu machine. also, as I said make sure the following line within sshd_config is set to the same static IP of the machine.

ListenAddress

---

### Post by berndtsson on 2012-12-12
> **dannyboy79 said:**
> did you set your sshd_config to listen on something other then 127.0.0.1 so you can connect to it from outside your lan?
...
 as I said make sure the following line within sshd_config is set to the same static IP of the machine.

ListenAddress

My ListenAddress was commented in sshd_config, however I was able to connect to it from outside the router before and the only actual change in sshd_config I made was add a Banner, which was a single line that didn't affect any other code.

So if my static ip is 192.168.0.137 
```
ListenAddress 192.168.0.137
``` Is this what I am supposed to try?

I will try doing that and edit results.


EDIT:
This is what happened when I added that line to the config.
```
 ssh localhost
ssh: connect to host localhost port 22: Connection refused
ssh 192.168.0.137
The authenticity of host '192.168.0.137 (192.168.0.137)' can't be established.
ECDSA key fingerprint is 7b:15:61:ec:2a:59:8e:be:59:e4:1f:d2:ca:4a:f9:24.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.0.137' (ECDSA) to the list of known hosts.
V'a'lkommen hem! :-)

```

So localhost doesn't work anymore, but connecting directly to the dhcp address works fine (inside the router).

When I tried with my IP (94.103.XXX.XXX), it tried to connect but nothing happened. No error, no nothing, just blank.

I don't know if it's actually worth finding the error before just reinstalling it all. I have backed up everything I need for the computer and I really want this computer to work like a server.

I think the only real reason to keep looking could be so that I learn the insides of linux, which in itself would be nice, but I'd rather do that while my other things are working!

Anyways, thanks for your help.

~Berndtsson

---

### Post by dannyboy79 on 2012-12-12
you can't connect via ssh to your external IP from inside your LAN. if you're trying to connect from outside your LAN, then you have to have forwarded port 22 on your router to IP address 192.168.0.137. 

why would you ever want to connect to your own ssh server from that server? ssh localhost is pointless.

---

### Post by berndtsson on 2012-12-12
> **dannyboy79 said:**
> you can't connect via ssh to your external IP from inside your LAN. if you're trying to connect from outside your LAN, then you have to have forwarded port 22 on your router to IP address 192.168.0.137. 

why would you ever want to connect to your own ssh server from that server? ssh localhost is pointless.

I tried it the first time around and it worked.

Anyways, I have re-installed Ubuntu on my computer and I have changed from DMZ to port forwarding.

Everything is working fine (for now) so I guess whatever error I had made was undone!

---

### Post by dannyboy79 on 2012-12-12
you tried it the first time because Listenaddress was set to 0.0.0.0 which means to listen on any IP which is less secure. But think about it, when are you ever going to ssh into your own machine? NEVER.

Im glad you got it working but IF everytime something doesn't work like you want you do a reinstall, you're going to be wasting a ton of time and not really learn anything.

---

