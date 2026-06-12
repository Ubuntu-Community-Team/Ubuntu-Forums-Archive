---
title: "How to conect to a network"
date: 2011-06-21
forum: Networking &amp; Wireless
---

### Post by miguelpires on 2011-06-21
Hello,
I'm new to Linux. I install 11.04 in my laptop, and now i wana test the 11.04 in my office network.
We have a server, that shared the database off our programs in a SAMBA drive. All the others workstations have windows instal and use that databses to work in the programs we have.
What i'm traying to do is conect my 11.04 to that network, share files with the others PC, and work in the programs i need like in a win worksation tru wine/crossover. 
My main problem is that i don't know how to conect to the network and see the other workstations.
Tk in advance for any help you can provide to me.
Miguel
PS: Sorry the bad english

---

### Post by spynappels on 2011-06-21
Can you give some more details? For example:

How do you want to connect? Wired or Wireless?
Is there a DHCP server on the network, or are IPs statically assigned?
Does your network have an internal WINS and/or DNS server?

Normally I'd say just plug it in and see whether it connects, but that is dependent on a DHCP server being present on the network.

---

### Post by Beacon11 on 2011-06-21
Assuming you were successful in getting online on the computer, you should be able to open up Nautilus and browse to Network. There you will be able to access samba shares on the network. In order to share files via samba, right click the folder you're wanting to share and hit Properties, then the Sharing tab. When you check the box for sharing, it will probably prompt you to install the software necessary for hosting a samba share.

---

### Post by miguelpires on 2011-06-21
Hummm... Tk's. I can access the internet via cable, i can't see the work stations. 
Hummm.. I think i don't use nautilus... I'm going to try to figure that out and then came back for more info if i need. Thanks

---

### Post by miguelpires on 2011-06-22
Thank's to both. 
Now i can see the Network!!! 
Now another issue:
I've some programs from windows that I need to work with. I can and install the program's in wine, but now i need to configure, in the program, the place wher the database is.
In all workstations with windows we have the drive "Z:" to the place wher we have the databases. 
My question is, how i do that in wine?? Its possible?
Regard's
Miguel Pires
Z. Folder is another computer

---

