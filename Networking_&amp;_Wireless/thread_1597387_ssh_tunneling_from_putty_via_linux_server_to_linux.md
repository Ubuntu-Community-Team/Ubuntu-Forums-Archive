---
title: "ssh tunneling from putty via linux server to linux machine"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by cajahop on 2010-10-15
So as it stands in the thread title I want to accomplish the following:

I want to make a ssh tunnel from machine 1 (WinXP, putty)
via server (Ubuntu, OpenSSH )
to machine 2 (Ubuntu, OpenSSH) which (!!) is reversly connected to the server ( machine2 forwards its port to the server with ssh command: 
ssh -R PORT2BEFORWARED:localhost:22 serveruser@servername ) - that means that server doesn't know about machine2 real address.

So its an akward situation yes. 
Maybe I could use Ubuntu on machine1 as plan B, so please write any suggestions you have.

thx

---

