---
title: "Connect ubuntu clients to samba sever (Domain Conect)"
date: 2011-07-15
forum: Networking &amp; Wireless
---

### Post by Kasun2005 on 2011-07-15
Hi All,

I want to convert whole network windows to ubuntu... i got ubuntu 11.04 for my client machines and Cent OS for Server machine.... to authenticate username and passwords i use LDAP Server... The problem is i cannot connect my client to the server... If windows we can add machine into the domain... how can i connect like that on ubuntu...?? please help me please... i'm in big trouble..... i want step by step instruction...

---

### Post by idlemind324 on 2011-07-15
Hi,

Did you do this live on your production equipment?

To get you up and running is it possible to use LDAP for authentication and NFS to get files to your machines? This would exclude samba and the setup may be easier then.

Tim

---

### Post by Kasun2005 on 2011-07-16
Tim,

Thanks for your reply... can't we use samba server domain connection..? or else give me some step by step instruction to set up to connect to a samba domain like windows domain...

---

### Post by idlemind324 on 2011-07-19
Good point. You can use Samba to connect linux hosts. Most people's viewpoint on an all Linux network would be to eliminate Samba although technically you should be able to do it without an issue.

I would recommend you review two documents:
[LIST]
[*][https://help.ubuntu.com/community/OpenLDAPServer]("https://help.ubuntu.com/community/OpenLDAPServer")
[*][https://help.ubuntu.com/community/LDAPClientAuthentication]("https://help.ubuntu.com/community/LDAPClientAuthentication")
[/LIST]

You will need to start their to get your authentication sorted out.

Next you will want to tackle file sharing and possibly something like automount, I'd recommend you utilize NFS for this. Below I put some notes on getting at least file sharing up and running if you are in a bind still.

Now if you are doing this in a production environment and you just need immediate file access you can utilize ubuntu's remembered connections option and enable SSH on the server. You can then use a SSH file connection between each workstation and the server to quickly setup your file access to get you on the ground running.

---

