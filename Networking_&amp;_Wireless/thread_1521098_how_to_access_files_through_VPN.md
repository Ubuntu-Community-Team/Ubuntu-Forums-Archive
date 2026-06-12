---
title: "how to access files through VPN"
date: 2010-06-30
forum: Networking &amp; Wireless
---

### Post by julianb on 2010-06-30
My system reports it successfully connected to the VPN at my workplace (pptp / windows server). So I had to enter my username and password in the VPN configuration screen, etc. My machine has Ubuntu 10.04.

I tried to find out how to open the files on the server. In windows, after opening the vpn I would go to this location in the file manager:

\\company-fs1\Users\Julian_b

this would show me the files I am looking for. 

in the linux terminal, and the Nautilus file manager, these locations do not exist. 

I tried using mount.cifs to mount this location and it didn't work
(fails with these messages : mounting the DFS root for a particular server not implemented yet
no ip address specified and hostname not found)

How do i get to these files on the Windows share?

---

### Post by SlugSlug on 2010-06-30
try use 'Connect to' and then connect to windows share (or samba)

---

### Post by alcapone-g on 2013-03-04
in shell type:
smbclient -U remote-user_name //ip-remote-computer/remote-share
you get prompt for password for user-on-remote-computer
type password
hit enter
you get 
smb>  now you type dir to get list of dir ar different command
to exit smb> type exit

---

