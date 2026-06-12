---
title: "Having trouble on samba share"
date: 2009-12-21
forum: Networking &amp; Wireless
---

### Post by drdanielfc on 2009-12-21
Hello,
  I recently set up an Ubuntu machine because, well, its awesome :). The only thing I can't seem to get working is the samba sharing. I'm using a clean install of 9.10 and am trying to access a Windows 7 share from another computer in the house.

I CAN access the computer via 'smb://192.168.1.103/' in nautilus, but I CANNOT use the computer name (which would be nice) and only the open shares work. The password-protected ones ask me for the user+pass and regardless of what I put in it just pops up another prompt afterwards. I need to keep the shares password protected.

The last part not working is the smb:/// view. I see the WORKGROUP but when I go to open it I get the error "Unable to mount location" "Failed to retrieve share list from server"

In synaptic a search for "samba" shows that I have these installed:
libsmbclient
libwbclient0
samba
samba4-clients
samba4-common-bin
samba-common
samba-common-bin
smbfs

Perhaps I'm missing a package?

Thanks ahead of time,
   Dan

---

### Post by dmizer on 2009-12-21
Please see the 6th link in my sig, as well as this post [http://ubuntuforums.org/showpost.php?p=8524499&postcount=45](http://ubuntuforums.org/showpost.php?p=8524499&postcount=45)

---

