---
title: "Samba: Problem seeing shares from Apple machines"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by rozen on 2009-11-28
Hi,

I seem to be very confused over my samba configuration. I have a home network consisting of 2 linux boxes Atlas (ubuntu 9.10) and Ajax using an older version of Kubuntu, an XP box and two Apple machines running Snow Leopard. Both atlas and ajax are running samba.

All machines on the network can see home directories on ajax and ajax can see the shares on atlas when I use the command

smbclient //atlas/rozen 

however, when I issue that command on an apple machine (mini)

I get the error message:

Connection to atlas failed (Error NT_STATUS_BAD_NETWORK_NAME)

My XP machine also fails to find a network path to \\atlas\rozen.

I have scoured the forums for information and I have inserted into the atlas smb.conf the line:

  netbios name = atlas

I booted from the install CD installed samba and was able to see the machine from mini, an Apple machine. So maybe something changed as a result of an update. I recollect that there was an update to samba.

I would certainly appreciate any suggestion.

Thanks in Advance,
Don

---

