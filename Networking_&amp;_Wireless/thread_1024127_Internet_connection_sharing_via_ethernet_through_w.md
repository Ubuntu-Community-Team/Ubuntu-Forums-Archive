---
title: "Internet connection sharing via ethernet through wireless connection"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by sharikiov on 2008-12-28
Sorry if this has already been posted, I've been searching for a long while and unable to find anything on this particular issue.

My internet connection is provided through my building as free wireless, and they only allow us to have one connection.

I've currently got an ubuntu box that I have been using this with, but wish to add other devices.

So, what I want to do is have my connection come in via the wireless and then run through my ethernet card to a router or hub to provide connections to other devices.  I have found a lot of resources explaining how to do this with 2 ethernet cards and they seem rather simple.

However, the problem that I am running into, is that as soon as I plug any kind of ethernet into my ubuntu box, it ceases to use the wireless connection and reverts back to trying to use ethernet for my outside internet connection.

Is there a way to change priorities on this so that it will still use the wireless for my outside internet and then have my ethernet card serve for the internal network I've created?

Also a little side issue, if anyone has any ideas, one thing I've found great is that somehow ubuntu seems to get around a cap they have in place for the network.  In Windows XP the connection seems to max out at 50-60k/s, but in Ubuntu I can pull up to 500-600k/s regularly.  I've used the machine on other wireless networks in XP and it works fine.  Any ideas?

Thanks so much,

Sharik

---

### Post by dmizer on 2008-12-29
As to ICS, try this: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

Please let me know if you have any difficulty following that.

---

### Post by sharikiov on 2008-12-29
Thanks for the reply.

That is a great resource, I found that earlier and it is actually the first one that I tried.

The problem is that as soon as I plug in the ethernet cable from the computer to my router the wireless connection stops working.

Ubuntu then begins trying to use the ethernet connection as the primary connection, and the wireless just craps out.

---

### Post by dmizer on 2008-12-29
Are you still using network manager to manage your network?

---

### Post by sharikiov on 2008-12-29
Yeah, for the wireless connection.  Should I set up the wireless connection manually, and forget network-manager all together?

---

### Post by DonovanM11 on 2009-01-07
I was having the same problem when I plugged in an ethernet cable. I opened Network Connections and clicked Edit for eth0. The first checkbox says connect automatically, uncheck that and it should work. Also, if you're still having trouble getting your sharing to work, I took the commands of the website and made a script out of it. I'm set up so that my wireless internet comes through eth1 and is shared through my wired ethernet port, eth0, so you will have to make those changes. Then on my XBOX 360, I have the network setting set up like this:

IP address: 192.168.0.2
subnet mask: 255.255.255.0
Gateway: 192.168.0.1 (ip address assigned to eth0)

Primary DNS: 192.168.1.254 (ip address of my wireless router)
Secondary DNS: 192.168.0.1 (ip address of eth0)

Hope this helps. I have had some problems with Moderate NAT connection,  but after I forwarded ports 88 and 3074 to my laptop, they disappeared.

---

### Post by dmizer on 2009-01-07
> **sharikiov said:**
> Yeah, for the wireless connection.  Should I set up the wireless connection manually, and forget network-manager all together?

Sorry, I missed your reply earlier.

I suggest disabling network manager: [https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager](https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager)
Make sure gnome's network management tool is installed:
```
sudo apt-get install gnome-network-admin
```
Then you can manage your network connections (including wireless) at System > Administration > network

---

### Post by mr_vodoo on 2009-02-25
> **sharikiov said:**
> Thanks for the reply.

That is a great resource, I found that earlier and it is actually the first one that I tried.

The problem is that as soon as I plug in the ethernet cable from the computer to my router the wireless connection stops working.

Ubuntu then begins trying to use the ethernet connection as the primary connection, and the wireless just craps out.

Hello,

I have exactly the same problem. As soon as I plug in the ethernet cable the Internet stops working. Dmizer recommends disabling network manager and using gnome's network management tool but this has not got WPA support, and I connect to wireless via a WPA access point.

I would appreciate if anyone could help

Many thanks

---

### Post by dmizer on 2009-02-25
Here's how to connect to WPA without Network-Manager: [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

