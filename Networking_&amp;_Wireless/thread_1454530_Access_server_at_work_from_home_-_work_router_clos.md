---
title: "Access server at work from home - work router closed"
date: 2010-04-14
forum: Networking &amp; Wireless
---

### Post by carlossousa on 2010-04-14
Hello everyone,

I've bee doing some googling but came up empty handed. I installed a ubuntu server at work that I need to access from the internet.
The problem is that I dont have access to the router so I cant reroute any ports.
The server does however have access to the internet, so in theory, I would need some kind of vpn client that would load up a connection, but would have to use port 80 and not the traditional 1193.
The ideia would be a little like teamviewer or logmein but none of these are available for linux.

Any help would be appreciated.

Carlos

---

### Post by Iowan on 2010-04-14
Your IT department is OK with the arrangement? Some might view it as a security liability.

---

### Post by carlossousa on 2010-04-15
Hello,

The ideia would be to prove a concept and create a counteracting mechanism I would implement at the firewall or proxy level, or on a ids machine in the middle situation.



internet ------- ids machine ----- router ----- switch
                                                ||||||
                                                uuuuuu  (users)
                                                123456

Carlos

---

### Post by 7h3d4rk0n3 on 2010-05-14
I think your answer lies in TeamViewer, which has recently been made for  Linux. It allows you to remotely access any computer in which you have  it installed on. You can also create an account and have a partner list,  which makes connecting to multiple computers very easy without having  to remember the access numbers for separate computers. Hope this helps.

------------------------------------------------------------------------------------------------------

Derik

AKA: ThedarKOne

---

