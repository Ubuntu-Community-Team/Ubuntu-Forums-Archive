---
title: "Accessing internet outside of home network"
date: 2012-01-16
forum: Networking &amp; Wireless
---

### Post by W@@dy on 2012-01-16
You don't need to use a DNS server for this right? It just makes it easier to access it by giving it a name to type in instead of a bunch of numbers?

How come I can't access my machine outside of my home network then?
There aren't any firewalls denying it (on anything, router, modem, machine), but when I click "Remote Desktop" on Ubuntu it says "Your desktop is only reachable over the local network."

And indeed, I have tried connecting out of network, and it won't work.
I've tried this at two different houses actually, and it won't work. For any machine.
I'd say it's an ISP thing, but one house uses Time Warner, and the other uses Verizon DSL

Home Network access works perfectly.

So what gives? How can I get it to be accessed out of home?

---

### Post by jsra on 2012-01-17
Hi,
if you have router you must forward ports to desired machine for remote desktop, port 3389.

---

### Post by jonobr on 2012-01-17
Ok, so if your accessing your home machine using an IP address instead of DNS, then the IP address must be the public IP address of your home connection.
Usually there is an IP address assigned to one side of your router thats public and can be seen by the rest of the world.

Its like your home number, street address , city and country.
Using that gets you to your house.

However, the home network is like a room in your house.

So, if your home is in the US and your in Japan and say, take me to room 2, that makes no sense in the outside world.

The internal network schemes are usually something like 192.168.x.x or 10.10.x.x or 172.18.x.x and so on.

If you try to connect using these it wont work.

As the second poster said, if you got to the public IP of your router and you tell your router to forward packets on the RDP port number, that will work so long as your ISP is not blocking this traffic.

one last thing on DNS.

above is all Ip addresses and hard to remember.
All DNS does is to associate an IP address to a name.
All websites are really IP addresses, however, DNS makes it easy to lookup the number using a name,

So as you said, putting in the number is the harder way to do it, but will work.

---

### Post by W@@dy on 2012-01-17
Haha sorry, I should have beena  bit more technical in my post.

I do know the difference between an internal IP and External IP.
And port forwarding was done correctly.

This is where I don't understand things.

With no firewalls on router or modem, having my router port forwarded, and trying to connect using the external IP address, the connection times out.

I used WireShark to check for the attempted connection, but there's no sign of it anywhere.
It's like the request never even reaches the house.

The only thing I can think of is that all the ports are set to "Stealth Mode", but as I understand it, port forwarding should allow connections to get through despite this.
"Stealth Mode", however, would explain why connection attempts time-out with no response.

---

### Post by jonobr on 2012-01-17
Hello there


as mentioned, if you run tcpdump on your ubuntu box and you dont see packets when you ssh, then either your ISP is blocing or your router is not forwarding.
Either way, the problem is outside the ubuntu box.

Also, sorry for the juvenile analogies.... 
I tend to either over or under do them:-)

---

