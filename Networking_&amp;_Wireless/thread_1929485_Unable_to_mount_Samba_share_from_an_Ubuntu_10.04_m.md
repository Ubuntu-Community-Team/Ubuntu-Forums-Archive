---
title: "Unable to mount Samba share from an Ubuntu 10.04 machine on any Ubuntu 11.10 machines"
date: 2012-02-22
forum: Networking &amp; Wireless
---

### Post by ianchai on 2012-02-22
I have Samba share from a Ubuntu 10.04 machine which I seem to have no problems mounting in Windows XP running in VirtualBox.

However, when I try to mount it directly in Unity, whether using the nautilus smb://name command or by double-clicking on the icon in the network browser -- it always times out with "unable to mount location" "failed to retrieve share list from server"

I have verified this on two different 11.10 machines. 

I have no idea where to look for the solution. Vice versa (that is, mounting the Samba shares from the 11.10 machines on the 10.04 machine) works fine.

---

### Post by ianchai on 2012-02-22
> **ianchai said:**
> I have Samba share from a Ubuntu 10.04 machine which I seem to have no problems mounting in Windows XP running in VirtualBox.

However, when I try to mount it directly in Unity, whether using the nautilus smb://name command or by double-clicking on the icon in the network browser -- it always times out with "unable to mount location" "failed to retrieve share list from server"

I have verified this on two different 11.10 machines. 

I have no idea where to look for the solution. Vice versa (that is, mounting the Samba shares from the 11.10 machines on the 10.04 machine) works fine.

I found the answer:
[http://askubuntu.com/questions/74789/failed-to-retrieve-share-list-from-server-error-when-browsing-a-share-with-nau](http://askubuntu.com/questions/74789/failed-to-retrieve-share-list-from-server-error-when-browsing-a-share-with-nau)

Gord Nickerson said:
> The error message is 'failed to retrieve share list from server' so it cannot browse a Windows 7 pc or a Ubuntu 10 pc or a mac desktop pc.

smbtree lists all the shares from machines on the network

so off to /etc/samba and we sudo pico smb.conf

The name resolve order uses hosts files first and broadcasts last and it is commented out! Maybe we change that to:

name resolve order = bcast host

and then restart the servers with service smbd restart and service nmbd restart

Works! This is an awful mistake to make in an upgrade. Upgrade should not break what is working, particularly something as important as networking. Good thing i recall the manual work you had to do to get samba working back in redhat 5 and 6. 

---

