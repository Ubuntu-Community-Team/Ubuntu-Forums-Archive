---
title: "[SOLVED] Caution - could be a stupid linkstation quesion"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by geekyhawkes on 2008-12-18
Hi;

i have just replaced my (rubbish) Freecom NAS with a buffalo linkstation live.  I intend on using SMB to set up some shares, but having no windows machine available i have no idea what the IP address of netbios name of the linkstation live is. 

Can someone steer me to how i might find this out please?

Thanks;

Geeky

---

### Post by geekyhawkes on 2008-12-18
Anyone?  There must be some kind of "network neighbourhood" or Find computers on network function in ubuntu?

---

### Post by nixscripter on 2008-12-18
My suggestion would be try pinging everything from the Terminal:

```
ping -bc 1 255.255.255.255
```

and see if it answers.

---

### Post by Iowan on 2008-12-18
You might try **nmblookup -T '*'** or **nmblookup -S '*'**.
**smbtree** is another option.

---

### Post by jonobr on 2008-12-18
wonder oif your arp table contains anything interesting

in a terminal type 'arp'
it should have hardware address and names.
You may also be able to look at the log in your router to match mac addresses in the arp to ip.

nixscripter has a good idea, it will send a message to all machines and ask them to respond.

If you know its a 192 address assigned you could limit the broadcast to 192.168.1.255

---

### Post by Iowan on 2008-12-18
> **geekyhawkes said:**
> Anyone?  There must be some kind of "network neighbourhood" or Find computers on network function in ubuntu?From **man smbtree**:>  smbtree  is  a  smb  browser program in text mode. It is similar to the "Network Neighborhood" found on Windows computers.  It  prints  a  tree with all the known domains, the servers in those domains and the shares on the servers.

---

### Post by geekyhawkes on 2008-12-20
THanks for the tips guys.  Strangly the buffalo didnt respond to the broadcast message, but neither did my existing NAS?  Im trying to find out if my wireless router (orange livebox) allows me access to its dchp settings so i can find the ip that way.  Any other thoughts?

---

### Post by geekyhawkes on 2008-12-20
Incase anyone else finds themselves with this problem, this is how i solved it;

I installed wine and then ran the buffalo setup cd with wine.  This allowed me to install the nas manager software and run it with wine.

All is now well with my nas, thanks for your help guys

---

### Post by nixscripter on 2008-12-20
Great. Please mark the thread as solved (under the Thread Tools menu).

---

