---
title: "Method for splitting network (specific problem)"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by arsenic23 on 2009-02-20
Ok I have an odd network setup I need to achieve and I'm hoping someone could give me a pointer or two.  [COLOR="Silver"]( I've tried several different things but keep reformatting in failure. )[/COLOR]


What I need to do is have a small network split in two through a single PC with two NICs.

eth1 will need to be 192.168.1.24
eth0 needs to serve DHCP and DNS in the range of 10.0.0.24-255
eth0 needs to also share the internet that is coming in from eth1

The PC that is splitting the network needs to be on the 192.168.1.x network and be able to ssh into 192.168.1.23 .

Computers on the eth1 side need to absolutely not have access to the eth0 side.


Any help would be appriciated as beyond simple home networking I'm completely inexperienced.

---

### Post by superprash2003 on 2009-02-20
well for the internet connection sharing part you coul use this [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by arsenic23 on 2009-02-20
> **superprash2003 said:**
> well for the internet connection sharing part you coul use this [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

Thank you, but I've tried that and several variations of it.

I can get the internet shared, but then the PC it is shared through ends up on the wrong network or both of the networks end up being able to comunicate.

Basically I have a primary network, with sensitive stuff on it that needs to share the internet and only the internet with another network.  The machine that is sharing the internet needs to be on the primary network.

---

### Post by arsenic23 on 2009-02-20
Ok, let's say I share the internet that way. 
Now I have the networks interacting and I'm no next to nothing about iptables.

What would be the best way to stop computers on the shared section from being able to comunicate with computers on the primary network.

Let's just say I want to block access to all IPs between 192.168.1.3 and .255 for all of the PCs that are getting the internet through the shared connection.

---

### Post by arsenic23 on 2009-02-21
Ok, I've gotten this kinda working now.

I can get all of the networking stuff working alright using iptables and dnsmasq.  I have the network split through the PC with a DHCP acuired IP address on the primary side and a static IP on the restricted side.  Then I have iptables set to block all but a few connections on the machine.

It works (well enough), but for some reason I can't get it too keep a static IP on the one connection.  No matter what I do (using the network manager or ifconfig) I can't get it to not be set to DHCP when I boot.  I've also caught it switching over to DHCP over night.

Any ideas ?

---

### Post by Perryg on 2009-02-21
> **arsenic23 said:**
> Ok, I've gotten this kinda working now.

I can get all of the networking stuff working alright using iptables and dnsmasq.  I have the network split through the PC with a DHCP acuired IP address on the primary side and a static IP on the restricted side.  Then I have iptables set to block all but a few connections on the machine.

It works (well enough), but for some reason I can't get it too keep a static IP on the one connection.  No matter what I do (using the network manager or ifconfig) I can't get it to not be set to DHCP when I boot.  I've also caught it switching over to DHCP over night.

Any ideas ?

I usually get around the network manager problems by manually editing the interfaces file under network.  Then edit the resolv.conf file for dns.

---

### Post by arsenic23 on 2009-02-21
> **Perryg said:**
> I usually get around the network manager problems by manually editing the interfaces file under network.  Then edit the resolv.conf file for dns.


Thanks, but even after manually setting the IP in interfaces **and** disabling the network manager I still don't get an IP address on the connection wihout manually opening a terminal and 'ifconfig eth1 $IP'.  

I wonder if this is my punishment for being lazing and using firestarter instead of manually figuring out how to setup iptables....

---

### Post by Perryg on 2009-02-21
> **arsenic23 said:**
> Thanks, but even after manually setting the IP in interfaces **and** disabling the network manager I still don't get an IP address on the connection wihout manually opening a terminal and 'ifconfig eth1 $IP'.  

I wonder if this is my punishment for being lazing and using firestarter instead of manually figuring out how to setup iptables....

I am not fimiliar with firestarter.  Does it run as a deamon?  Does it require you to put addresses in it to operate?  If so can you disable it now that you have figured out what to do and see if that helps?  Seems to me that running without it and doing some routing statements would work as well.  Just a thought!

---

### Post by arsenic23 on 2009-02-22
> **Perryg said:**
> I am not fimiliar with firestarter.  Does it run as a deamon?  Does it require you to put addresses in it to operate?  If so can you disable it now that you have figured out what to do and see if that helps?  Seems to me that running without it and doing some routing statements would work as well.  Just a thought!

Firestarter is just a frontend for iptables.  It doesn't really run at all, it just gives a simplified GUI setup for iptables.  ( *Or I'm fairly sure that is what it does.* )

I'm thinking, as a guess, that something to do with dnsmasq is forcing the DHCP onto eth1 regardless of how it is setup.  I have no idea how to fix it though.

---

### Post by Perryg on 2009-02-22
> **arsenic23 said:**
> Firestarter is just a frontend for iptables.  It doesn't really run at all, it just gives a simplified GUI setup for iptables.  ( *Or I'm fairly sure that is what it does.* )

I'm thinking, as a guess, that something to do with dnsmasq is forcing the DHCP onto eth1 regardless of how it is setup.  I have no idea how to fix it though.

Oh!  
I see now and here I have been doing this manually.  
Silly me!  Should have looked for an easier way.

Thanks

---

### Post by arsenic23 on 2009-02-26
Sharing the connection with Firestarter and firewalling it did eventually work.  I'd made a typo or two in my /etc/network/interfaces file.


[COLOR="DarkRed"](( Can I not mark this thread as solved ?? ))[/COLOR]

---

