---
title: "Ubuntu 11.10 LDAP clients"
date: 2012-02-28
forum: Networking &amp; Wireless
---

### Post by lisanels47 on 2012-02-28
I'm trying to find a solution for a small office of 6 computers.

All computers running Ubuntu 11.10 with all the updates.

One system running LDAP, and it works fine. (I'll call it the server) Able to create users groups etc.

I'd like to manage all the users and groups on the server, and not have to manage a bunch of users on all the workstations.  

If there's a better solution than LDAP, I'm willing to change.  

Ideally, I want any user to be able to logon to any workstation.  The home directories can either be on the local workstations, or the server, I don't care.  They don't really use their home directories.

Any help would be greatly appreciated.

Thanks,
Lisa

---

### Post by lisanels47 on 2012-02-29
Update:  well, my client computers can do ldap searches, but I have not found info on how to get lightdm to authenticate to the ldap server... 
I get errors in the syslog:

lightdm: pam_ldap: ldap_simple_bind Can't contact LDAP server
hsic-55 lightdm: pam_ldap: reconnecting to LDAP server...

But I'm able to ldap searches from the client computer.

---

### Post by lisanels47 on 2012-03-26
I got it working.  I used autofs5 to auto-mount their homedirectories via NFS, and when setting up the ldap server, it defaults to (manager,example,net).
I had to change manager -> admin
example -> mydomain
net -> com
ldapi://  -> ldap://):P

Then it all worked very well. Now my clients all authenticate via ldap and have their home directories.

Final issue is how to have the clients see what permissions are on the server.  Currently everything shows huge numbers for the owner and group of all files and directories.

---

### Post by lisanels47 on 2012-04-13
All is well except that I'm testing Ubuntu 12.04TLS, and there is no option to logon using "Other".  So I'm unable to logon to my ldap server, only the local logon's are allowed...

---

### Post by newbie-user on 2012-04-16
Add the line greeter-hide-users=false to /etc/lightdm/lightdm.conf to get rid of the user list. That way there's only a text field for the user name and you don't have to worry about clicking "other".

---

### Post by lisanels47 on 2012-04-16
Thanks!  Exactly what I needed, but it needs to be set to "true".

---

### Post by newbie-user on 2012-04-16
> **lisanels47 said:**
> Thanks!  Exactly what I needed, but it needs to be set to "true".

Oh, oops, sorry. Yes, it needs to be set to true.

---

