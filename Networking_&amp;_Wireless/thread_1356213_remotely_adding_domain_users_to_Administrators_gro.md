---
title: "remotely adding domain users to Administrators group on a Windows domain machine"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by Tee.Gee on 2009-12-15
Hi,
 
I'm trying to remotely add domain users to the Administrators group of a Windows domain machine using the 'net' command from a ubuntu PDC (samba 3.4.0-3ubuntu5). This works fine for Windows 2000 and XP, but Windows 7 (Enterprise) won't let me do it.
 
 I can use the following command to list the members of the Administrators group:
 net rpc group members Administrators -U "machine\admin" -S machine
machine\admin is amongst the results, so this user should be able to add members to the group and in fact, if I log on to the machine as this user, I can add any domain user to the Administrators group.
 
 When I try to add members to this group with this command:
 net rpc group addmem Administrators "domain\user" -U "machine\admin" -S machine
 Windows 7 says: Could not add domain\user to Administrators:
 NT_STATUS_ACCESS_DENIED
 
 I've been looking around in the security policies, asking on the samba mailing list but I couldn't find anything useful.
 
 Any ideas how to make this work?
 
 Cheers,
   Tom

---

