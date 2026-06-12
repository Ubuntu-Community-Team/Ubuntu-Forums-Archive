---
title: "samba over vpn works on android not on windows"
date: 2011-06-06
forum: Networking &amp; Wireless
---

### Post by daviid on 2011-06-06
We just set up a vpn & samba server and are running into this problem. 

we can log into the vpn and can ssh, http, ftp in the various servers on the internal network. however when trying to view Samba/Windows shares over any windows machine, they fail to connect. BUT we can vpn in on any android device and using a samba app view the Samba & Windows shares on any server we try. 

If im logged in the network internally, there does not seem to be a problem. Only if we VPN in from the outside.

---

### Post by collisionystm on 2011-06-06
> **daviid said:**
> We just set up a vpn & samba server and are running into this problem. 

we can log into the vpn and can ssh, http, ftp in the various servers on the internal network. however when trying to view Samba/Windows shares over any windows machine, they fail to connect. BUT we can vpn in on any android device and using a samba app view the Samba & Windows shares on any server we try. 

If im logged in the network internally, there does not seem to be a problem. Only if we VPN in from the outside.

You need to make sure the WINS address is being assigned. do an ipconfig /all in the command prompt of your windows machine to check what address is being handed out for wins/netbios

---

### Post by daviid on 2011-06-06
got it to work by disabling wins server in smb.conf

---

### Post by daviid on 2011-06-07
well it worked for a bit. logged out of the vpn and back in and now it wont. didnt change a thing.

---

### Post by doas777 on 2011-06-07
samba over a vpn is a real pain.

try specifying the full host name of the remote PC:
\\AppSrv.VPNedDomain.org\shareename
and see if that helps. 

also, remember, enabling wins in smb.conf instructs the server to act as the wins server rather than to be a client of it.

---

### Post by dgourd on 2011-06-26
I am getting the same problem.  Samba works on the local network fine.  I can VPN in to my network from my android phone and access the remote files on my Ubuntu PC.  VPN works fine on my Windows 7 laptop, but I can't access any of the shared files on my Ubuntu PC.  A WINS address is being handed out to the server, and even specifying the full host name wont work.  Enabling and disabling wins server in smb.conf did nothing.

---

