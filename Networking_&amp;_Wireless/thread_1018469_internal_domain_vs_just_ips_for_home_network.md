---
title: "internal domain vs just ips for home network"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by jimmy the saint on 2008-12-22
What are the advantages of having an internal domain as opposed to just using ip addresses?  I have tried researching this, but everything I find is either a tutorial for setting up dns for the outside or extremely technical and not helpful to me.

Thanks
JTS

---

### Post by Iowan on 2008-12-22
Depending on your definition of "domain", I suppose you could ping, connect, etc., by name instead of IP.  Another version of "domain" would have authentication on one machine.  You'd need to "log in" only once (but sudo would still be in place). For me, it would primarily be for education - to see how it's done.

Just my opinion - which in no way reflects reality...

---

### Post by andguent on 2008-12-22
I'm with Iowan. There are two different versions of a "domain" you can have in a home network. Unfortunately they do blend and overlap at times. For basic home use, both can definitely be classified as "only fix it if you really want to break it" type items.

Making a DNS based domain often makes it easier for computers to connect to each other on the LAN. If fully functioning, it means that you could setup pc01.myhomeDNSnamethingy.local to translate to the equivilant IP address, etc. If all computers are setup to belong to myhomeDNSnamethingy.local, then often you can drop that altogether and just ping pc01, file browse to it, and otherwise connect to it without needing to know its IP address.
** For this type of functionality, I use dnsmasq (should be in apt). Just watch that it likes to do DNS & DHCP at the same time. It can do either one or both if you want it that way.


For file security reasons and user authentication, you can setup a security domain using a "Domain Controller" that is a central point of security. Once all workstations are set as domain members, most requests for file access need to be approved by the domain controller. This means that it is easier to control who has access to what files. Nearly all large companies do this type of setup to keep the new people out of the HR documents, etc. If any of this sounds complicated, good. It is complicated, but very worth it in a business environment.
** For this type of functionality, you can setup Linux to act as a domain controller using Samba. A second option is SMB-LDAP found in the smbldap-tools package. Both are on apt.

Have fun breaking stuff. :)

---

### Post by jimmy the saint on 2008-12-22
Wow.  I'm thinking of a two week break project.  That all seems interesting, but more of a summer learning experience.  Am I wrong in assuming thats a bit overkill for home network primarily serving media and doing backups?

---

### Post by cariboo on 2008-12-22
Depending on how many computers you have on your network, it may be easier just to alias the ip address to hostname in /etc/hosts eg:

```
 cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	jack
192.168.1.1	router
192.168.1.200	willy
192.168.1.202	minibuntu
```

Jim

---

### Post by jimmy the saint on 2008-12-22
so if I understand that correctly, I would add that host file to every computer and the when I typed "willy" in a browser address bar, ssh, or ftp the appropriate computer would be connected to?

---

### Post by Iowan on 2008-12-22
Yes, it's probably overkill... but so was DHCP on a home network, although appliance routers have made it pretty simple.  I put some of the components (slapd) on my server some time ago, but haven't actually made it a domain controller.  Guess I'm worried about the point-of-no-return. I'm still somewhere between "If it ain't broke, don't fix it" and "If it ain't broke, take it apart and fix it anyway".

---

### Post by jimmy the saint on 2008-12-22
I hear you.  I gotta say, I switched to Linux around the time fiesty.  I switched primarily because I found myself becomming way to good at fixing/reinstalling/disifecting/isolating/.... XP.  I hated spending so much time dealing with so many issues on several computers.  Now I find myself spending a whole lot of time on the computers, but I'm exploring and learning as opposed to repeating the same irritating steps over and over again.  That sounds like an anti-windows statement, but it's more of a pro-Linux/Ubuntu one.  Its becoming an engrosing hobby and I actually enjoy the time I spend working on them.  Computing is fun again!!
ok, I'm done.  
Thanks for the info!

---

### Post by andguent on 2008-12-23
> **jimmy the saint said:**
> so if I understand that correctly, I would add that host file to every computer and the when I typed "willy" in a browser address bar, ssh, or ftp the appropriate computer would be connected to?

To answer your question, yes. I would say "update" the file instead of "adding" the file, but close enough.

I'm completely with cariboo907. You can definitely add the appropriate lines to each hosts file so then they can connect using the name instead of the IP. That is the quick and dirty option and will work fine, it just may need to be maintained a bit.

Also keep in mind that Windows has a similar hosts file. On XP it sits in C:\windows\system32\drivers\etc.

Setting up home DNS (like the dnsmasq app) really only gains you the options of DNS automatically updating itself as new computers are added to the network, or IP addresses change on individual computers due to DHCP. 

The educational part of it is probably more significant then the immediate technical benefits. If you REALLY wanted to have some fun with custom DHCP/DNS, you could later delve into some PXE network booting and revive those 300mhz boxes sitting around...

---

### Post by jimmy the saint on 2008-12-23
HAHA it's funny you mentioned the 300MHZ boxes.  My fiance just convinced me to get rid of my old 300MHZ AMD K6-2 box with 128MB Ram and a VooDoo3 3000.  I built that with the money I got in basic training, and it was screaming at the time!  *sigh*

---

