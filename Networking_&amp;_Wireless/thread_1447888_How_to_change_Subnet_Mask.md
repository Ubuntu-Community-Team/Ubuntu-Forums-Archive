---
title: "How to change Subnet Mask"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by BurakUeda on 2010-04-05
Hi,
Linux newbie here.

I am using ubuntu Lucid and connected to a network with windows machines.
Our network admin changed some settings in the network, and all machines need to change their subnet masks to access local machines (e.g. I am getting "unable to mount" message when I try to connect other Windows PC's on the network.)

If I open the connections panel, and "Edit" the "Auto eth0", I can get:
IPv4 Settings -> Method -> Manual -> Addresses -> Add
And I am pretty sure I will put new subnet mask address into "Netmask" box, what to put others? Namely:
IP Address, Netmask, Gateway
and below:
DNS Servers, Search Domains

I can get some info about my network connection by right clicking network icon on the panel, and select "Connection Information"

Tried to fill manual settings with some of those info (the ones made some sense to me) but I still cannot mount windows network drives, plus my internet connection dies.

So, is there any way to change Subnet Mask "ONLY", without touching any other setting.

Thanks.

---

### Post by BurakUeda on 2010-04-06
Problem is solved, kind of...
Before, I was accessing other machines by clicking Places->Network->MSHOME
And I saw all the machines as icons, with the machine names. Now, when I double click MSHOME I get either an error message that the place cannot be mounted, or nothing, an empty folder.

I just tried to enter the machine name directly to the Nautilus bar, like:
smb://machine_name
and voila! I am inside the machine...

strange...

---

### Post by capscrew on 2010-04-06
> **BurakUeda said:**
> Problem is solved, kind of...
Before, I was accessing other machines by clicking Places->Network->MSHOME
And I saw all the machines as icons, with the machine names. Now, when I double click MSHOME I get either an error message that the place cannot be mounted, or nothing, an empty folder.

I just tried to enter the machine name directly to the Nautilus bar, like:
smb://machine_name
and voila! I am inside the machine...

strange...

Not so strange at all.  What this means is that you can query the individual machine (host) but there is no browse list available for you to browse all of the shares at one time.

Your first question might be answered in a different way.  Are  you are getting the IP address via DHCP.  If so, the DHCP will supply the correct subnet mask along with the IP address.  You need to do nothing.  Maybe that is why you can still communicate with the samba shares and the internet.

To see what your current IP address and subnet mask is you can use this from the command line in the terminal:
```
ifconfig -a
```

If you do need to change it, can you tell us what is was and what you need to change it to?  What is the new network IP number? and what was it originally?

---

