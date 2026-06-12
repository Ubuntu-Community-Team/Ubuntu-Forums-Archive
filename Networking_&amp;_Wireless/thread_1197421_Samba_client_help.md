---
title: "Samba client help"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by michellez on 2009-06-26
I'm trying to connect to a NAS on the network (Linksys NSLU2 with standard but latest firmware).

When trying to connect I get the following (I know the details are fine, also tried specifying the username, workgroup etc):
> shell@duck:~$ smbclient -L //192.168.45.5
Password:
session setup failed: NT_STATUS_LOGON_FAILURE

I have a feeling I know what the problem may be because on Windows 7/Vista machines that I connect to it I have had to change the security policy so the passwords aren't encrypted that are sent to it (!). Is the same going on here? Done some google but can't suss out how to get around it.

Thanks,
Shell

---

### Post by michellez on 2009-06-26
Also I wasn't sure which forum to post this in, as it does relate to the client and not the server. Is there a better one...?

Thanks,
Michelle

---

### Post by Iowan on 2009-06-26
Does the Linksys have the option to use encrypted passwords? (might be hiding as Win95 compatibility)

---

