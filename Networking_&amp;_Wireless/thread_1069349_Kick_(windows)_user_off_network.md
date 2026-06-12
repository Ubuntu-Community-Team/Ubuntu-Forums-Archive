---
title: "Kick (windows) user off network?"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by Deutscher Alex on 2009-02-13
How would I go about kicking a user off my wireless network?

---

### Post by TombKing on 2009-02-13
Is your network secured in any way at all? That's going to be the best and simplest way to keep other users out.

I know I have the choice of my network which is passworded or depending on what the neighbors have powered on 3 other completely open ones.

---

### Post by yther on 2009-02-13
Log into the admin page of your wireless router, find their connection and revoke their lease?  Then blacklist their MAC, I would think.

Of course, TombKing is right, if you're running an open network you'll have freeloaders.  ;)

---

### Post by Deutscher Alex on 2009-02-13
Yes it's password protected and all.

I'm looking for a simple way to kick a family member off the network without physically unplugging their wireless card or anything

---

### Post by yther on 2009-02-13
Well then, my first sentence would apply.  :)

Seriously, my WLAN router (by SMC) has a page where you can see all connected machines listed, and it shows IP address, MAC, and machine name.  That's enough for me to identify all of my devices, and if I wanted to boot one all I'd have to do is check a box and push "Revoke Lease."  That would disconnect the device.

To prevent it from reconnecting, I'd go into the DHCP configuration and block it from connecting... at least, I *think* there's an option for that.  If not, a firewall rule blocking all traffic to and from it would work.

---

### Post by Deutscher Alex on 2009-02-13
> **yther said:**
> Log into the admin page of your wireless router, find their connection and revoke their lease?  Then blacklist their MAC, I would think.


Would simply blacklisting their MAC work?
I'm navigating the admin page of the router, and i can't see how to do either of those things.

I can see the "attached devices" (computers/printers on network) and their MAC addresses, but there's nothing to edit on this page...
I guess I'll google how to blacklist on the NETGEAR router

---

### Post by Deutscher Alex on 2009-02-13
> **yther said:**
> Well then, my first sentence would apply.  :)

Seriously, my WLAN router (by SMC) has a page where you can see all connected machines listed, and it shows IP address, MAC, and machine name.  That's enough for me to identify all of my devices, and if I wanted to boot one all I'd have to do is check a box and push "Revoke Lease."  That would disconnect the device.

To prevent it from reconnecting, I'd go into the DHCP configuration and block it from connecting... at least, I *think* there's an option for that.  If not, a firewall rule blocking all traffic to and from it would work.

Ok awesome, i'll go back to google & find specifics for my router

---

### Post by TombKing on 2009-02-13
> **Deutscher Alex said:**
> 
I'm looking for a simple way to kick a family member off the network without physically unplugging their wireless card or anything
In that case you would have to go even more secure and have a list of allowed mac addresses, or at least thats how mine would set it up as it will only whitelist allowed cards.

---

### Post by Deutscher Alex on 2009-02-13
Problem solved :)

1. Added all our computers onto the "allowed" list (Wireless Station Access List)
2. Created a txt file with all device names + mac addresses for re-adding computers
3. Delete select computers from "allowed" list
4. Turn "Access Control" on (activate "allowed" list)

Could having MAC addresses in a txt file pose a security problem? ie If someone manages to hack my computer and figures out I have them stored in a txt file


EDIT: I seem to have forgotten how to declare a thread [SOLVED] :(

---

### Post by TombKing on 2009-02-13
> **Deutscher Alex said:**
> 
Could having MAC addresses in a txt file pose a security problem? 
Well if you get hacked then you have bigger problems.

But as I work at a large company with some pretty solid security requirements. We can keep a password file (and trust me we need one for all the damn different accounts that get used for login once a year at best) on a network share that is locked down only to the users that need to see the data.

If you want you can encrypt the file or put it in a hidden directory or something. Some kind of minor security by obscurity would probably work well enough for a home network.

---

