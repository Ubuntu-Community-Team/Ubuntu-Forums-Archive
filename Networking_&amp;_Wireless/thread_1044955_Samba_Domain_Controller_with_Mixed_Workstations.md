---
title: "Samba Domain Controller with Mixed Workstations"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by chownsb on 2009-01-19
Here's the situation.  Our network has a Samba domain controller (running Ubuntu 5.xx or 6.xx) and we access the domain using Windows XP workstations.  The Samba domain authenticates our XP machines and sets up some drive mappings.  This has worked fine for years.  I am not the one who originally set this up but I have a general understanding of how it works and a pretty solid understanding of Linux.

Now we would like to introduce an Ubuntu workstation to the network and use the Samba domain controller to authenticate the new machine's users.

I have searched long and hard and come up blank.  There seem to be many "Join Windows domain with Ubuntu" threads but I'm not even sure if that's what I'm trying to do since the domain controller is actually Samba.

I figure since I'm trying to join Linux with Linux essentially that maybe there's a quick and easy way of doing this that I haven't found yet.  If anybody can steer me in the right direction I'd be very grateful.



Thanks!

---

### Post by dmizer on 2009-01-20
Does this help? [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

If your domain is Samba controlled, then you'll have to teach your Ubuntu client to play by Samba rules. Otherwise, you could use LDAP, but you'd have to configure your server to host LDAP.

---

### Post by chownsb on 2009-01-20
Thanks...that brings us to my next question.  Is a Samba domain considered Active Directory?  I was trying to use Likewise-open at one point but wasn't sure if it was even Active Directory I was trying to join.  With Likewise-open I got firewall port issues but to my knowledge there is no firewall between the workstation and server.  They're both on a local network with no internal/software firewalls that I'm aware of (plus the Windows clients work fine).

---

### Post by dmizer on 2009-01-20
I am far from an expert on domain controllers, but I think that would depend on what kind of domain controller your samba server is emulating. I am not positive, but I think an NT domain is not AD and Win2003 domain is AD.

Here is some information I've found for joining an NT domain:
[http://ubuntuforums.org/showthread.php?t=5409](http://ubuntuforums.org/showthread.php?t=5409)

---

