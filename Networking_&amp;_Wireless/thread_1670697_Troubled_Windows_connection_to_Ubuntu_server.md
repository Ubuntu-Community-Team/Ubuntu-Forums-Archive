---
title: "Troubled Windows connection to Ubuntu server"
date: 2011-01-19
forum: Networking &amp; Wireless
---

### Post by molinus on 2011-01-19
This post started under Server Platforms, but I think it may be more appropriate to put it here.
I am about to pull out whatever hair I have left...

I have a single LAN with 8 Windows (XP Pro, XP Home & Win7), 2 Linux and 3 Mac units, and one standalone Ubuntu fileserver (using Samba) and webserver hosting several intranet websites.

All IPs are static and all units & server have internet connectivity.

1) Mac & Linux work perfectly with Ubuntu server.
2) I successfully pinged (200 pings using both name & IP) each unit to all the other units (Win to Mac, Win to Win, Win to Linux & vice versa).
3) But I cannot ping the Ubuntu Server from any Windows unit except.......

.......I did the following testing randomly from all Windows units, and here is a representative sample of the results:
200 pings of 32 bytes to the server:
Results:
The first 188 pings timed out.
Only the last 12 replied.
time to reply - 3263ms for the first one, two at 1ms, one at 250ms, and the other 8 at 1ms.
Then I pinged 50 - all replied, and I connected to the Ubuntu server shares and intranet websites.
Went to get a cup of coffee.
Connection gone.
Pinged 50 - all timed out.
Went to bathroom.
Pinged 50 - timed out except last 6 pings.
And so on...

Trick is, during this whole week, the Macs and Linux units have never once lost connection with the server...
It has to be something with how Windows talks to Ubuntu, but I am at a loss.

I was wondering if it might be some kind of network speed differential problem, given the link aggregation I set up for the server. But the Macs & Linux zoom on it, and I configured it for auto-negotiation. And I get the same results whether a Windows NIC is 100 or 1000 mbs.

Another possible suspect: for network browsing, I have Samba set up as WINS server, Domain Master, Local Master, Preferred Master, OS level 33, and allow all hosts.

Does anyone have an idea, or should I be talking to Rod Serling?

Thanks much in advance.

---

### Post by koszta on 2011-01-19
wow that is just so weird... try describing your topology more .. (what switches do you use and are those L2 only or also L3? , ...) do you use any firewalls anywhere?

---

### Post by molinus on 2011-01-19
Star topology - hybrid nodes - L2/L3 - Dell PowerConnect 2824

Yes, there are firewalls, but set up correctly - I disabled FWs, but no difference.
Besides, unless there is an operating system or program problem, a firewall either allows a specific connection or it doesn't. For Windows, most of the time the connection is not there, but sometimes it is there. 
And the connection is always there for Macs & Linux through the same firewall/configuration.

---

