---
title: "Help me setup samba"
date: 2010-09-16
forum: Networking &amp; Wireless
---

### Post by thealmightyone on 2010-09-16
I am trying to make my netbook (which runs eeebuntu 3.0, which is based on Jaunty) accessible from my desktop (which runs windows 7 64-bit) for both read and write access, with no need to login, and vice versa.

I managed to get this to work with a **lot** of trial and error, but recently had to reinstall Eeebuntu, and nothing I do gets the share working as it used to. I have installed samba and samba-common, and their dependencies.

My smb.conf is as follows:
[HTML]
[global]
workgroup = WORKGROUP
security = share

[Home_folder]
path = /home/andy
writeable = yes
browseable = yes
guest ok = yes
[/HTML]

The majority of the time, when I try to access the netbook, I get the "The network path was not found." error. Very occasionally, I manage to get in, only to find I don't have write access. I have changed the smb.conf file at least 40 times, trying to get into the netbook, and to enable write access.

Similarly for when I try to access shared folders on my windows desktop from my netbook, the majority of the time I get the "Unable to mount location" error, but very occasionally I get in. However, there is still a problem, as for one of these times, I tried transferring a large file, which simply stalled at around 550MB - I had conky open, and could see that network traffic had dropped to 0.

I have noticed that if I right-click a folder, go to 'Sharing Options', then enable sharing, the option to enable 'Guest access' is greyed out - I thought this might be related, as I recall this option being available before I reinstalled Eeebuntu.

---

### Post by pricetech on 2010-09-16
When you installed Samba, did you install system-config-samba too ??  It's a GUI for configuring Samba which might make the job easier.

I'd start there.

---

