---
title: "Diskless clients..."
date: 2008-12-03
forum: Mythbuntu
---

### Post by colin.mcgregor on 2008-12-03
I am working my way through the issues of setting up a diskless client under Mythbuntu. My current issue is the IP address of the database server. If I on the FE/BE box the IP address is 127.0.0.1 (localhost) all is well on the FE/BE box. On the other hand attempting to connect from the diskless client with either the localhost address or the real IP address of the server (in this case 192.168.2.101) and things do not connect.

The firewall does not appear to be in operation, so I assume I am missing something simple/stupid...

Suggestions?

Thanks

Colin McGregor

---

### Post by SiHa on 2008-12-03
127.0.0.1 will only work for a BE/FE, as you have found

If you want to connect a remote fontend, on the 1st page of 'General' in mythtv-setup, you need both the local backend and master backend set to the 'real' IP address of that machine. Then the diskless client should connect.

Edit: I've also found that with multiple machines it's a good idea to give them static IP addresses. I had assumed my router dished out fixed IP's .101, 102, 103 etc... in order of the number of the port that was connected, until it swapped them one day and my backend disappeared.

HTH

Simon

---

### Post by colin.mcgregor on 2008-12-06
SiHa noted:
  
[I]127.0.0.1 will only work for a BE/FE, as you have found
 
 If you want to connect a remote fontend, on the 1st page of 'General' in mythtv-setup, you need both the local backend and master backend set to the 'real' IP address of that machine. Then the diskless client should connect.[/I]

Yes, I understand that, BUT when I put in the 'real' IP address, in this case 192.168.2.101 on the diskless client it will not connect to the database on the FE/BE box. 

So, the firewall doesn't appear to be running, what else could be causing grief? Thanks.

[I] Edit: I've also found that with multiple machines it's a good idea to give them static IP addresses. I had assumed my router dished out fixed IP's .101, 102, 103 etc... in order of the number of the port that was connected, until it swapped them one day and my backend disappeared.
[/I]

Well, I've used the assign MAC address to IP address feature on my little router box. Means I can update stuff like name servers at one point without a login to every box. This can make hardware updates a bit more of pain however...

---

### Post by majoridiot on 2008-12-07
> **colin.mcgregor said:**
> SiHa noted:
  
[I]127.0.0.1 will only work for a BE/FE, as you have found
 
 If you want to connect a remote fontend, on the 1st page of 'General' in mythtv-setup, you need both the local backend and master backend set to the 'real' IP address of that machine. Then the diskless client should connect.[/I]

Yes, I understand that, BUT when I put in the 'real' IP address, in this case 192.168.2.101 on the diskless client it will not connect to the database on the FE/BE box. 

So, the firewall doesn't appear to be running, what else could be causing grief? Thanks.

[I] Edit: I've also found that with multiple machines it's a good idea to give them static IP addresses. I had assumed my router dished out fixed IP's .101, 102, 103 etc... in order of the number of the port that was connected, until it swapped them one day and my backend disappeared.
[/I]

Well, I've used the assign MAC address to IP address feature on my little router box. Means I can update stuff like name servers at one point without a login to every box. This can make hardware updates a bit more of pain however...

if your FE/BE was not originally set up for remote mysql access, then you need to enable it.  the
easiest way is to go into mythbuntu control centre under the "system services" tab and enable
"mysql service" toward the bottom of the pane.

apply, and you should be good to go... assuming that the both the FE/BE and remote FE have the 
actual IP addy of the backend, as discussed above.

---

