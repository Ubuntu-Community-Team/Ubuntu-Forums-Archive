---
title: "NFS setup - Ubuntu 10.04.3 Server"
date: 2011-09-02
forum: Networking &amp; Wireless
---

### Post by mytinytown on 2011-09-02
I have a serious issue with setting up NFS. I have 2 different servers, then main server is a tower with Ubuntu 10.04.3 Server on it and the back up is an old SG20 with Ubuntu 7.10 on it. I am having very SLOWWWW Samba issues and was told to use NFS, so I am trying to set it up.

My Windows PC has Windows Services for UNIX 3.5 client on Win XP Pro.
Main server 10.04.3 has both NFS server and client
Back up server 7.10 has both NFS server and client.
Main server and back up server both work with each other. So I can access the Public folders on both server from either server, just like I wanted to and just like it should.

The Windows PC has access to the Public folder on the back up (7.10) server.

The problem is when I try gain access to the main server with the windows PC I can not.

Both main and back up servers are set up the same other the the version on Ubtunu used. When trying to access the main server with the Windows PC here is what happens:
I open Windows Explorer.
Expand on the NFS Network and right click on Favorite LAN and add Host there. I add it just like I added the Host for the Host for Back up server. (I also tried adding by right clicking on NFS Network and adding it there too)
It adds either way.
I the click on the added Host and see the NFS Export.
I The right click on the exported folder and either Windows Explorer locks up 100% or I add it as a mapped drive, then windows explorer locks up 100%. It locks so badly that I have to shut the PC down by holding the power button. Of course the Ubuntu server doesn't even flinch.

The above is the exact way I set up the back up server which works perfectly.

I do disable Samba while doing all this, otherwise it causes issues.

I hope someone can help me!!

---

