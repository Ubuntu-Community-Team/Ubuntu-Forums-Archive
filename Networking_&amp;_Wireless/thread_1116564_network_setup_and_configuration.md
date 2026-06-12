---
title: "network setup and configuration"
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by jrperpetu on 2009-04-05
Hi! I set-up Ubuntu 8.10 as host for 3 windows box for my kids.

i am using Zyxel ADSL modem and D-link DES1008D switch, both unmanaged box.

my hardware connection (all straight cable) was this:

**adsl modem>>> Ubuntu box (host)>>> network switch>>> clients (Windows box)**

my Ubuntu box has 2 NIC.

is my hardware set up correct?

how about configuring for printer, folder and Internet Connection Sharing with the clients?

Please help!


Jose
Philippines

---

### Post by sully101 on 2009-04-05
Your best way to tackle the problem is going to be doing one thing at a time. Start by getting your linux machine to connect to the internet. You will really have to be more specific. what exactly isn't working?

---

### Post by Iowan on 2009-04-05
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a help page for ICS.

---

### Post by confusedstingray on 2009-04-05
just some points

the outline you have setup means that the ubuntu box has to be on all the time to access the internet from the other machines.
is there a reason for this setup?

also some config info would be helpful 
are you running DHCP?
or static ips

the setup your after is not that hard to setup just need some base points and the rest is easy.

I have a internet connection sharing 5 ubuntu machines, 2 windows and 2 wireless connections 
with parent  control for the kids machines 
be glad to help you

---

### Post by superprash2003 on 2009-04-05
for file and folder sharing you need samba [http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html](http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html)
for printer sharing [http://www.prash-babu.com/2008/05/how-to-setup-network-printer-or-share.html](http://www.prash-babu.com/2008/05/how-to-setup-network-printer-or-share.html)

---

