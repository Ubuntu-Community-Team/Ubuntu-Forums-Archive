---
title: "Suse Authentication in Windows 2008 Active Directory"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by tiagoskid on 2009-04-07
Hello,

I am trying to set up a network with a Windows 2008 Server, using AD, I'm trying to authenticate in Suse with a Windows username( username@windowsad...), for it to work I have to have the user created both in the Windows AD and in Linux,it shouldn't have to be like this, I think. 

I gave each a different password and I'm logging in with the Windows password, so I know it is getting information from the AD, but it takes forever to log in, around 5 minutes, and this error keeps popping up meanwhile,

Apr 2 18:33:15 Susy sshd[3839]: nss_ldap: failed to bind to LDAP server ldap:// 10.154.59.51: Invalid credentials
Apr 2 18:33:15 Susy sshd[3839]: nss_ldap: failed to bind to LDAP server ldap:// windowsad-dc.windows-ad.testes.loc/: Invalid credentials
Apr 2 18:33:15 Susy sshd[3839]: nss_ldap: reconnecting to LDAP server (sleeping 64 seconds)...

I'm using kerberos alogside with ldap.


Any idea what is going on???

Thankyou!

---

