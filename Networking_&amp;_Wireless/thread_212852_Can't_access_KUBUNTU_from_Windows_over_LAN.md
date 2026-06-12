---
title: "Can't access KUBUNTU from Windows over LAN"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by Hank Montgomery on 2006-07-10
I have several WIN-XP machines including one named OFFICEXP.
All in P2P workgroup behind a belkin router providing NAT & DNS.
All boxes are running WIN-XP SP2 firewall.
I am running IIS and MySQL servers on the host named OFFICEXP.

I have installed KUBUNTU (with network host name = KUBUNTU)
KUBUNTU is also behind the router & has same workgroup name.

I have installed SAMBA and MySQL on KUBUNTU.
The same userid and password is used on ALL boxes.

From the router:
  The WIN-XP machines all show their hostnames and IP addrss.
  KUBUNTU server shows IP address but shows "(null)" hostname.
  The table shows all in the same subnet.

I can ping between WIN machines by host name or IP address.
I can only ping to/from KUBUNTU by IP address.

Neither the KUBUNTU web browser nor MySQL will find OFFICEXP.
But I can log into the OFFICEXP MySQL server using IP address.
I can NOT log into KUBUNTU MySQL from WIN even with IP address.
(yes I can logon to KUBUNTU MySQL from localhost and yes I did set the id up to be accessed from any host - just as was done on OFFICEXP)

The KUBUNTU file browser can see OFFICEXP in the workgroup, can open OFFICEXP, and can access OFFICEXP shares.

From OFFIXEXP Windows Explorer can NOT access KUBUNTU Shares. 
Windows Explorer shows KUBUNTU in the workgroup.
Attempting to open KUBUNTU prompts for Userid & Password.
Providing my userid & PWD fails and a The windows dialog box comes back with KUBUNTU\userid in the userid field but attempting to login that way also fails.

I suspect a network or firewall config problem in my UBUNTU installation but I have searched for similar posts on forums and can not find any matches.  My head is getting sore from banging the brick walls.  PLEASE HELP.

Thanks in advance.

---

### Post by jferrando on 2006-07-10
Try to comment the line:

#bind-address           = 127.0.0.1

in the file /etc/mysql/my.cnf. This will allow access to mysql from other hosts.
With SAMBA, you need to create samba passwords for the users. Have you tried:
$ sudo smbpasswd your_user_name

---

### Post by Hank Montgomery on 2006-07-11
Thanks jferrando,

Samba and MySql are now networking as expected.

That means I can move on to new Linux challenges ;)
like why my first reply to your post didn't stick  

Thanks again

---

