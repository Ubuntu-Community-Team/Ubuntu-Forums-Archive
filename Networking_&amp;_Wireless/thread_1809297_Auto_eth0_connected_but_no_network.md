---
title: "Auto eth0 connected but no network"
date: 2011-07-21
forum: Networking &amp; Wireless
---

### Post by sri429 on 2011-07-21
I am using BSNL broadband ISP and I am able to get network on windows os but not on my ubuntu.( I have a dual boot).

I see Auto eth0 connected from the notification but when i am pinging google.com it says unknown host.

can someone help me.... may be i am doing something silly here......

but beating my head for 2 days....

---

### Post by Bucky Ball on 2011-07-21
Are you using static IP address?

---

### Post by sri429 on 2011-07-21
> **Bucky Ball said:**
> Are you using static IP address?

nope...its dynamic.

---

### Post by sri429 on 2011-07-21
<bump>

---

### Post by Bucky Ball on 2011-07-21
Please wait twenty four hours before bumping. Sorry, I have no suggestions at this point. ;)

---

### Post by sri429 on 2011-07-21
bump

---

### Post by sri429 on 2011-07-22
can someone please help me here...

this is really killing me....

tried many things but nothing seems working....

---

### Post by Vienen on 2011-07-22
i have the same problem. i have to boot windows first to make ethernet work on ubuntu. any idea?

---

### Post by Bucky Ball on 2011-07-22
> **Vienen said:**
> i have the same problem. i have to boot windows first to make ethernet work on ubuntu. any idea?

Win and Ubuntu have nothing to do with each other so going down the wrong track there. Please post a new thread with a descriptive title to get better help rather than crash this one. It gets confusing trying to solve several issues at once. Cheers.

Post a link to new thread here if you like and we'll try help. ;)

---

### Post by docbop on 2011-07-22
why don't you open a terminal window and type /sbin/ifconfig -a.   That will show you what is or isn't configured.  If not configured try  sudo /sbin/ifconfig (name of interface) down   then sudo /sbin/ifconfig (name of interface) up.   See if recyling the nic it gets an IP.

---

### Post by Iowan on 2011-07-22
Can you ping your router?
Can you ping Google by IP address (74.125.225.49 is one address)?

---

