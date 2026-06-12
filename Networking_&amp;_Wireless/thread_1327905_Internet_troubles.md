---
title: "Internet troubles"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by The Funkbomb on 2009-11-15
I'm at my wits end with my slow internet.  I know most of you guys like to get away from trouble shooting here but I was hoping someone can help me trouble shoot my connection.

My Setup:

I have cable at my house.  Usually I get 10mb down and 2mb up.  I have two splitters on the line running into my house.  One goes to another room to a cable box.  The line that remains in the computer room is split again to a cable box and to the modem.  We have had this setup for years with no problems.  The splitters have been replaced not too long ago but way before these problems started.  An ethernet cable running from the modem to a netgear router (more on this in a bit).  One ethernet line running from the router to a desktop.  I have 4 other computers that connect wirelessly.  All of them are wireless G.

The Problem:

My internet is bad.  I just ran a speedtest from speedtest.net.  The server I'm hitting is in New York.  I'm just over the line in Connecticut.  The distance is maybe 60 miles.

Here are the results:

.59Mb/s down
1.26Mb/s up
29ms Ping

Yeah, bad...

The desktop that's wired is getting equally bad speeds.

Pinging my router:

Average response is 1.382ms  No packets lost.

What I have tried so far:

I called the cable company and he had me plug directly into the cable modem.  It shot up to 10mb/s down.  We both agreed that my router was bad.  It was an older WRT54GS.  I went out and got a WRT54GS2 and not only did my speed not improve, but this terminal was constantly getting dropped from IRC.  I returned the WRT54GS2 and got a Netgear WGR614 v7.  It's no longer dropping me from IRC but still the speeds are bad.

I replaced the ethernet line running from the modem to the router.  I tightened down all of the co-ax connections.

Things I have ruled out:

Routers.  3 routers all have the same result.
The computers.  No way are 5 computers breaking at the same time.
Ethernet cable.  The one running from my modem to my router is brand new.
Co-ax cables.  How come I'm getting a normal upspeed and a terrible downspeed?  And how come sometimes it shoots up to 10mb/s down?  Has anyone heard of a co-ax cable going bad intermittently and only affecting one stream?
The cable system itself.  I've tried at all hours.  On-peak and Off-peak.  Sometimes I get 10mb/s down on-peak (usually not) and I've gotten .5-1.5mb/s down at 2am.

Anyone have any ideas on what else I can try?

---

### Post by The Funkbomb on 2009-11-15
I plan on calling the cable company tomorrow and swapping out a cable modem.  I hope they don't give me grief.

They wanted to send a tech out but that's a last resort.  I really don't want to let a stranger into the house to dig through my cables.

One more thing.  Cable TV seems fine.

---

### Post by lisati on 2009-11-16
Re question @ [http://ubuntuforums.org/showthread.php?p=8325791#post8325791](http://ubuntuforums.org/showthread.php?p=8325791#post8325791) 

Isn't the internet related to networking?

---

### Post by running_rabbit07 on 2009-11-16
Do you have the IPs in both systems set to DHCP or static? If they are set to static, make sure both have their own IP and not the same IP.

If using wireless, have you tried changing which freq it is using? It is possible someone nere you is using the same freq for something.

Do you have security enabled? If you do not have security enabled, you may have a thieving neighbor.

---

### Post by running_rabbit07 on 2009-11-16
One quick way to see if your neighbors are stealing your connection is to install wireshark from the repositories and fire it up. Use ```
ifconfig
``` to see what your PCs IPs are and if you see another IP in the same range as yours moving packets, you have a thief.

Also take a look at the IPs of your systems and compare them to what you see in Wireshark. If any one system is constantly moving packets, yet you know it is supposed to be idle, it has a bad NIC. That would be enough to cause massive collisions and kill your connection speeds.

If your modem is working fine when directly connected, then it is not the problem.

Let us know if any of this rings a bell.

---

### Post by running_rabbit07 on 2009-11-16
One last thought that may seen way out left field, have you recently placed a high amperage appliance anywhere near your router? If so the EMI/RFI could be your enemy.

---

### Post by doccali on 2009-11-16
You're probably already aware, but 8bits = 1 byte, your cable speed is measured in bits, but DSLreports could be reporting in bytes, in which case, a 1+ MBps (Mega Byte per second) throughput is perfectly reasonable for a 10mbps (mega bits per second) connection.  Your ping speed is pretty good.

---

### Post by wilee-nilee on 2009-11-16
Turn the router off and let it reset the IP turn it on in 1-10 minutes this always works with router. If you have access to the router control from your computer there is usually a reboot tab turning it off manually does the same thing.

You should be able to get into the router with 192.168.0.1 in the browser bar.

---

### Post by The Funkbomb on 2009-11-16
> **running_rabbit07 said:**
> Do you have the IPs in both systems set to DHCP or static? If they are set to static, make sure both have their own IP and not the same IP.

If using wireless, have you tried changing which freq it is using? It is possible someone nere you is using the same freq for something.

Do you have security enabled? If you do not have security enabled, you may have a thieving neighbor.

Computer IPs are static and have not changed.  I double checked my DNS servers and they're still good.

I have changed my freq and it's not that.  The wired PC is affected too.

I have WPA enabled.  Thievery is not an issue since a few neighbors have absolutely no security enabled.  I've checked my router logs and no one else has connected.  

> **running_rabbit07 said:**
> One quick way to see if your neighbors are stealing your connection is to install wireshark from the repositories and fire it up. Use ```
ifconfig
``` to see what your PCs IPs are and if you see another IP in the same range as yours moving packets, you have a thief.

Also take a look at the IPs of your systems and compare them to what you see in Wireshark. If any one system is constantly moving packets, yet you know it is supposed to be idle, it has a bad NIC. That would be enough to cause massive collisions and kill your connection speeds.

If your modem is working fine when directly connected, then it is not the problem.

Let us know if any of this rings a bell.

My modem isn't working fine when directly connected.  It only did once, then it dropped.

> **running_rabbit07 said:**
> One last thought that may seen way out left field, have you recently placed a high amperage appliance anywhere near your router? If so the EMI/RFI could be your enemy.

Nothing has changed in the last eight months or so.  This problem started happening in the last week.

> **doccali said:**
> You're probably already aware, but 8bits = 1 byte, your cable speed is measured in bits, but DSLreports could be reporting in bytes, in which case, a 1+ MBps (Mega Byte per second) throughput is perfectly reasonable for a 10mbps (mega bits per second) connection.  Your ping speed is pretty good.

No, something is definitely wrong.  When a Youtube movie takes a minute to load a few seconds and then stops to load more, that's a problem.  Before, I could load a 10 minute youtube movie in a few seconds.

> **wilee-nilee said:**
> Turn the router off and let it reset the IP turn it on in 1-10 minutes this always works with router. If you have access to the router control from your computer there is usually a reboot tab turning it off manually does the same thing.

You should be able to get into the router with 192.168.0.1 in the browser bar.

Routers and modems have been rebooted countless times.

---

### Post by running_rabbit07 on 2009-11-16
Once you get the new modem, if the problems are still there, I would check to see if one of the hosts is doing a constant broadcast, caused by a NIC going bad.

---

### Post by The Funkbomb on 2009-11-16
I think (crossing fingers) that the new modem solved the problem.

I'm getting about 12 down now.

---

### Post by running_rabbit07 on 2009-11-16
> **The Funkbomb said:**
> I think (crossing fingers) that the new modem solved the problem.

I'm getting about 12 down now.

That is good to hear.

---

### Post by The Funkbomb on 2009-11-16
Thanks for your help though.  I'm going to give it 24 hours.  If it's still at acceptable levels, I'm going to say it's solved.

---

