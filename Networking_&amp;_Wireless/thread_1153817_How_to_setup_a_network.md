---
title: "How to setup a network?"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by Chetan26 on 2009-05-09
Hi ,
      Iam new to ubuntu.
      I have  got 4 computers (all on Ubuntu 8.1)  .
      I want to connect all these on a network with a groupname so that 
      they can communicate with one another.
      Can you  please help me setting up  my network?  

      Many Thanks


Chetan

---

### Post by Alias1407 on 2009-05-09
Just make sure that all of them are connected under the same router and they should all detect each other.

If you wish to view them....
Places-->Network

If you wish to share a folder....
Right click on the folder that you want to share and go 'Sharing Options..'


That should do it, unless you have a winblows computer on your network, in that case you will need to install Samba.

---

### Post by Chetan26 on 2009-05-09
Hi ,
        Thanks for  reply.
        I have got 4 ubuntu machines  and one windows machine.
        I  have installed  samba on one of the machines  and made it as server. Iam able to see only server machine and windows machine on network.
        Do I need  to add  all the Ipaddresses  of the machines on the network on the server machine. 
        
         Pls tell me how  does it work?


Regards
Chetan

---

### Post by superprash2003 on 2009-05-09
you could edit the smb.conf file ( /etc/samba/smb.conf ) and set it to the same workgroup as windows machine.. i think the windows machine by default is connected to a workgroup called WORKGROUP.. so make your linux machines to also join WORKGROUP . Frankly speaking you can use any name you wish.

---

### Post by Iowan on 2009-05-09
I don't understand Samba as well as I once did, but I suspect only the "servers" (machines with shares) will be visible.

---

