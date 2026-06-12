---
title: "How to restrict internet by time?"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by PerfectReign on 2009-12-12
I looked through the internet and on my wireless router. My son is using an older laptop of mine, which has 9.04 loaded.  (I haven't upgraded to 9.1 yet but will get there.)

I want to restrict his ability to access the internet without restricting his use of the compter by time. 

Let's say I want him to only be able to use port 80 traffic between 7:00 AM and 8:00 PM.

How does one go about this? 

I see this thread on this forum: [http://www.ubuntugeek.com/disable-internet-access-for-particular-user-in-ubuntu.html](http://www.ubuntugeek.com/disable-internet-access-for-particular-user-in-ubuntu.html)

However, that seems to restrict by user all the time.

---

### Post by spongypants23 on 2009-12-12
If you have a Linksys router, they have a built-in function for that.

---

### Post by PerfectReign on 2009-12-12
Thanks, that's what I thought and found supposedly on the intraweb: 

[http://support.dlink.com/emulators/di524_revc/help_adv.html](http://support.dlink.com/emulators/di524_revc/help_adv.html)


However, I cannot for the life of me see how to get his lappy working. It seems his MAC address changes and running /sbin/ifconfig gives me the same IP address as the router.

[FONT=Arial]**Filters** 
 [SIZE=2]Filters are used to deny or allow LAN computers from accessing   the Internet. Within the local area network, the unit can be setup to deny   Internet access to computers using the assigned IP or MAC addresses. The   unit can also block users from accessing restricted web sites.[/SIZE][/FONT]               [FONT=Arial]**Filter - IP Filters**
 [SIZE=2]Use IP Filters to deny particular LAN IP addresses from accessing   the Internet. You can deny specific port numbers or all ports for a specific   IP address. The screen will display well-known ports that are defined. To   use them, click on the edit icon. You will only need to input the LAN IP   address(es) of the computer(s) that will be denied Internet access.[/SIZE]
 ***[SIZE=2]IP[/SIZE]* **[SIZE=2]- The IP address of the   LAN computer that will be denied access to the Internet. You can also add   a range of IP addresses.
 ***Port*** - The single port or port range that will be denied access   to the Internet. If no port is specified, all ports will be denied access.
 ***Protocol Type***[/SIZE][FONT=Arial][SIZE=2]-   [/SIZE][/FONT][SIZE=2] This is the protocol type that will be used   with the Port that will be blocked.
 ***Schedule ***- This is the schedule of time when the IP Filter   will be enabled.[/SIZE][/FONT]               [FONT=Arial]**Filters - MAC Filters**
 [SIZE=2]Use MAC Filters to deny computers within the local area network   from accessing the Internet. You can either manually add a MAC address or   select the MAC address from the list of clients that are currently connected   to the unit.
 Select "Only **allow** computers with MAC address listed below to   access the network" if you only want selected computers to have network   access and all other computers not to have network access.
 Select "Only **deny** computers with MAC address listed below to   access the network" if you want all computers to have network access   except those computers in the list.
 ***Name:*** The name referencing the MAC filter.
 ***MAC Address: ***The MAC address of the computer in the LAN (Local   Area Network) to be used in the MAC filter table.
 ***DHCP Client:*** DHCP clients will have their host name and MAC   address listed here. You can select the client computer you want to add   to the MAC filter and click **Clone**. This will automatically add that   computer's MAC address to the **MAC Address** section[/SIZE][/FONT]

---

### Post by spongypants23 on 2009-12-12
It sounds strange that the MAC address changes, usually it's the IP that does that.

Have you tried setting a static IP in Ubuntu via network manager, then using that?

---

### Post by jobix on 2009-12-12
Another way to do this would be use the cron functionality to bring down your Ethernet interface and bring it up at regular pre-specified times. This can be done using ifup and ifdown. In your cron file, you'd have two lines (man crontab for exact syntax) along the lines of:

> ifup eth0 --- execute this everyday at 7:00 AM
ifdown eth0 --- and this everyday at 8:00 PM 

This is assuming your son doesn't know how to use ifup and doesn't use ubuntuforums.org :)

---

### Post by Iowan on 2009-12-12
The router would seem to be more bulletproof, but yet another option would be to use **cron** to selectively run **iptables** rules to block/unblock the ports (80 in particular). 
Some drawbacks: the machine would need to be on at the trigger times, resetting the clock could bypass restrictions, flushing **iptables** would also bypass the restrictions.

---

### Post by alexfish on 2009-12-12
Blocking ?,  is not an answer to the question

         children // by nature ask questions

  if you don't give an answer to  which they don't understand / RE: Blocking? without reason

   being " human"  they will look somewhere else

  they are "your children"

     you are their "parent"  and they  trust parent's

---

### Post by PerfectReign on 2009-12-14
> **spongypants23 said:**
> It sounds strange that the MAC address changes, usually it's the IP that does that.

Have you tried setting a static IP in Ubuntu via network manager, then using that?
Well, after making my other laptops completely unusable, I figured it out.

The reason teh MAC changed is because I was using a wired connection while the machine was in my office and a wireless now.  Different card.

As it is, I found some feature on my router to block traffic. Unfortunately, i succeeded in blocking ALL traffic out through the router for any wireless connection.

I'll go back and figure something later.

---

