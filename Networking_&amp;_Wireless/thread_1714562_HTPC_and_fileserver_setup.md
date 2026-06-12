---
title: "HTPC and fileserver setup"
date: 2011-03-25
forum: Networking &amp; Wireless
---

### Post by tirdyr on 2011-03-25
I wanna make a setup like the follwing but im not completely sure how to make it work.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=187094&stc=1&d=1301081896[/IMG]

What i need to work:
[LIST=1]
[*]Xbmc must be able to acces the internet, download small files from the internet etc.
[*]I might in the future wanna more XBMC boxes to that part of the network. so it must be easily configured on the clients
[*]The wired computers on the other subnet must be able to SSH to the XBmc Box.
[/LIST]

Server is a Ubuntu server 10.10 installation, with 2 network interfaces, i might add more roles to this server later on.

Im not sure how to go about this...

---

### Post by conneco on 2011-03-25
why not have the XBMC on the same LAN as everything else?

---

### Post by tirdyr on 2011-03-25
because the XBMC subnet is running gigabit, while the rest is ATM only using 100 M/bit...

---

### Post by conneco on 2011-03-25
You gonna talk host to host with crossover or is there another switch in there?

---

### Post by tirdyr on 2011-03-25
for now i will only talk with cross over, but i might wanna add a switch in so i can add more XBMC boxes to the gigabit network

---

### Post by conneco on 2011-03-25
What part dont you get?

---

### Post by tirdyr on 2011-03-25
how i give the XBMC an IP address that is accesibel from the general network.

---

### Post by conneco on 2011-03-25
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

that should do it

---

### Post by tirdyr on 2011-03-25
i cant believe that worked.. it was actually what i was thinking about, but didnt think it would work on diffrent subnets....

Ty very much

---

### Post by conneco on 2011-03-25
<arnie voice>No problemo</arnie voice>

---

