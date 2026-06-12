---
title: "need an fstab entry for my network"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by Heeter on 2009-04-08
Hi all,

I need to edit my fstab for a shared network drive. Samba has been enabled and the firewalls/apparmor are all disabled. I can "see" the "files" folder on my client when I use the "Connect to server" method.

Here are my specs:

The folder that is being shared on host IP is: //192.168.1.110/Files
The usernames for both host/client is: admin
The password for both host client is: password
Host is Ubuntu Server 8.10, Client is Ubuntu Desktop 8.10. Both 64Bit.
"Files" folder has been created in the home folder of the client machine.

Any other info anyone needs I will gladly supply.


Thanks in advance guys,


Heeter

---

### Post by compiledkernel on 2009-04-08
Using NFS would be just a bit easier in this scenario. If your willing to go a step further, take a read here. 

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

Then you can just add an entry to fstab for that NFS mount and share them between. No need for Samba use between two Ubuntu machines (or any other linux machine for that matter.).

---

### Post by Heeter on 2009-04-08
Great, Thanks for that idea, compiledkernel.

Heeter

---

