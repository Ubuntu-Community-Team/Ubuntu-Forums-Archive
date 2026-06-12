---
title: "Samba share not working between VMs"
date: 2012-04-18
forum: Networking &amp; Wireless
---

### Post by OliverHaslam on 2012-04-18
Hi

I'm trying to set up Samba on an Ubuntu VM, and then connect to it via a Windows 7 VM on the same host.

The Windows VM sees the share, but when I try and connect to it I am asked for authentication. I enter it, along with the domain name (ubuntubm\olivm) and my password, but then I get told that the user is not recognised.

Any ideas?

---

### Post by OliverHaslam on 2012-04-18
Success!

For some reason I needed to set an SMB password.

[smbpasswd -a username]

I'm not sure why I didn't need to do this with the host, but did with a VM. It's the same install of Ubuntu!

---

### Post by sc0g on 2012-04-18
You can configure /etc/samba/smb.conf so that you don't have to use smbpasswd in the future. Although I don't know which parameter it is off the top of my head. :-)

---

### Post by OliverHaslam on 2012-04-18
> **sc0g said:**
> You can configure /etc/samba/smb.conf so that you don't have to use smbpasswd in the future. Although I don't know which parameter it is off the top of my head. :-)

I assume that now I've set the password, that'll be that?

Any ideas why I've set this up on a host and a VM in twelve hours and had two different experiences regarding this?

---

### Post by bab1 on 2012-04-18
> **OliverHaslam said:**
> I assume that now I've set the password, that'll be that?

Any ideas why I've set this up on a host and a VM in twelve hours and had two different experiences regarding this?

There are many ways to set up Samba security.  In addition you can configure Samba to allow guests with no login needed.

For example, if you have set *security = share* there is no login needed.  Also if you allow *guest = ok* you can also have no login access.  With all configurations the Linux permissions are the final say on file and directory use.

---

