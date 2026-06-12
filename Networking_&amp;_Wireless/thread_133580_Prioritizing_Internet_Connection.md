---
title: "Prioritizing Internet Connection??"
date: 2006-02-20
forum: Networking &amp; Wireless
---

### Post by Razorback on 2006-02-20
I am wanting to know if you can set the priority of your different internet connections.  My current setup has two different ways of connecting: one thru my XP box using ICS via a NIC card and the other with an external dial up modem.  My NIC is setup using DHCP.  I have this setup so I don't always have to have the XP box connected or turned on for that mattter.  But if the network connection is active, my modem connection does not act correctly.  It connects, but doesn't seem to communicate.  If I disable the network connection, it works so I figure that when I use either connection, the ICS connection always has priority.  Please shed some light for this noob. Thanks.

---

### Post by bscbrit on 2006-02-20
What do you want it to do?  If the network is up it uses it, if not, then the modem will work.  You cannot use both simultaneously (well not easily) but why would you want to?

---

### Post by Razorback on 2006-02-20
Thanks for the reply. I don't want to use them simultaneously.  Since I am on dial up, I don't leave my connection up all the time.  I want to be able to use either connection with my linux box without having to disable settings.  Sometimes my wife or kids are playing games on the XP box without being connected and I want to use the modem to hook up to the internet.

---

### Post by bscbrit on 2006-02-20
Ok, I think the easiest way to do this would be to write a script which does the things that you currently do manually to switch from one to the other.  For example, if you usually switch off the network and then invoke a program to dial out, it might look something like this:

ifdown eth0
echo "Network disconnected"
dialout

Of course, this is very simplistic but the principle is good.  Having produced the script (see man bash and search on Google) you can always put a launcher on the desktop so that a single click does what you want.

Did that help or am I going in the wrong direction.....?

---

### Post by Razorback on 2006-02-20
I see what you are saying. I don't necessarily want to disable the NIC unless I would have to.  I talked to a friend of mine that mentioned that I should be able to set something that would use the modem as the primary connection and use the NIC when the modem connection wasn't active.  I am not sure how I can do that though.

---

### Post by bscbrit on 2006-02-20
There is a piece of software that does what you want for wireless and ethernet networks but I have never heard of one that does that for a modem.  Might exist though.....

And all you need to do to switch your network back on is

ifup eth0

---

### Post by Razorback on 2006-02-20
Thanks, I will look into it.

---

