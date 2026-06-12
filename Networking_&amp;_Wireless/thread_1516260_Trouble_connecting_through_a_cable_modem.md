---
title: "Trouble connecting through a cable modem"
date: 2010-06-23
forum: Networking &amp; Wireless
---

### Post by dupree_ on 2010-06-23
Hi I am using ububntu 9.10,and have a cable modem internet  connection.
All I have is an ethernet cable given to me,and when  plugged in a windows machine and fire a browser am redirected to default  login page where i can login,
but when i plug it into my linux  machine,i cant get the same done.
In network connections it doesnt  shows my autoeth0, i have deleted my existing dsl settings(not  autoeth0),made a new wired network,
i doubt what should i put into  MAC addrs field(i have put my machines mac given by lshw -c network.)
What  should I put in DHCP client id?
Anyways when i click on network  connections it says under my wired connections-device not configured  properly.
 Any help would be great.

---

### Post by Iowan on 2010-06-23
Some modems "lock onto" a MAC address, and must be reset before they will work with another machine.  
The MAC address from **lshw** *should* be the right one. My home Lucid machine has a blank DHCP client ID - although I'm not using cable...

---

### Post by dupree_ on 2010-06-25
Yeah but the problem here is I dont have access to modem..I guess it is with my local ISP.
All I am given is an ethernet cable.So how do i proceed in that case,as power cycling of modem wont be possible.

---

### Post by Iowan on 2010-06-25
> **dupree_ said:**
> All I am given is an ethernet cable.From where does the ethernet cable come (or... into what what does the other end plug)?

---

### Post by ieee488 on 2010-06-25
> **dupree_ said:**
> Yeah but the problem here is I dont have access to modem..I guess it is with my local ISP.
All I am given is an ethernet cable.So how do i proceed in that case,as power cycling of modem wont be possible.

There is no way that is the case. You **have** the cable modem in your house.

---

### Post by dupree_ on 2010-06-25
> ** 			 		 	 	 From where does the ethernet cable come (or... into what what does  the other end plug)?**

I have this ethernet cable coming in through my apartments window,and it runs overhead through the building..I guess the the other end probably goes into a router which is providing (ethernet) connections to other people as well..and from there a main cable might go to modem,which I am pretty sure is nowhere in my vicinty.
:(
Do i need access to modem?

---

### Post by CharlesA on 2010-06-25
You would have to figure out how the network is layed out and then deal with whoever manages it.

---

