---
title: "Un-google-able connection issue"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by bantab on 2009-07-16
I usually have great luck using google and man pages to solve any computer troubles, but I am frankly dumbfounded at how to even begin to figure out how to diagnose my problem on this one.  I am running ubuntu desktop updated to the latest jaunty release, and am trying to connect to my desktop periodically for a number of reasons, some being a VNC connection and an SSH connection. My computer is connected to the local network via a wireless WPA encrypted connection.  The address is assigned by the DHCP server on my router, but is reserved and therefore static. Upon a refresh of my wireless connection, I am able to connect to my desktop fine from other computers, but after a short period I am unable to connect (note that the behavior is not indicative of WPA key refreshing). However, my desktop is still connected to the network even after I am unable to reach it from other computers on the network, as I am able to connect to the internet from the desktop. If I then ping the computer on the network from the desktop, that computer is able to connect to the desktop. 

An example of a typical sequence:
Refresh wifi
Ping from network to desktop successful
Ping from desktop to network successful
Wait a short time
Ping from network to desktop unsuccessful
Ping from desktop to network successful
Ping from network to desktop successful


Any advice on what logs at which to look, or what services might be causing this behavior?  I feel like this behavior is not the intended default as SSHing to an idle computer seems like a fairly ordinary task.  However, if it is default behavior, do you have a recommendation on how to achieve the desired behavior of connecting to an idle compouter. Any information would be greatly appreciated, even a possible google search term, as I have been unable to come up with anything that would give me relevant information. Thank you so much!

---

### Post by bantab on 2009-07-17
A simple suggestion for a unique search term would be really helpful.

---

### Post by shredkingj on 2009-07-17
If you run the arp command on the other PC's after trying to connect, do you see an entry for your Ubuntu box?

---

### Post by bantab on 2009-07-17
Thanks for the help! I get (incomplete) instead of a mac address from a mac computer (after an outgoing ping), and no entry from a windows computer.  The router is an appliance, and my first inclination would be to think the problem is there, but I have run VNC servers on this machine when it was running windows with no trouble. Thanks for the additional diagnostic... I am trying to figure out what this might indicate, and I would appreciate any insight you have.

---

### Post by shredkingj on 2009-07-17
This indicates that if all devices are on the same network, the Ubuntu box is not responding to arp requests.  If the Ubuntu box is on a different subnet, then I would suspect arp cache corruption on the router.  What do you mean by refresh wifi, are you power-cycling your router?  If it is the router, a power-cycle would clear the arp cache, and you can probably manually clear the arp cache on the router, too.

I would setup a tcpdump or wireshark capture on the Ubuntu box.  You should see something like this (substituting your real IP addresses and MAC address):

arp who-has x.x.x.x tell x.x.x.y
arp reply x.x.x.x is-at 00:00:00:00:00:01

---

