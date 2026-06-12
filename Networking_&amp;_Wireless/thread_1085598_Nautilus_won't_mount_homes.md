---
title: "Nautilus won't mount homes"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by rick71 on 2009-03-03
When I try to access Homes on my Samba server (Hardy, fully updated) from an Ibex workstation (also fully updated) Nautilus returns an error:

Unable to mount location
Failed to mount windows share.

However, it will mount another share on the same server. Windows users can access their home directory through Network Neighborhood. Linux users can access their home directory with smb:/servername/username. Does anyone have any ideas on how to fix this?

Below are the relevant portions of the smb.conf:

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
[homes]
   comment = Home Directories
   browseable = yes
   

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes
   writeable = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
   valid users = %S

[Shared]
	writeable = yes
	path = /shared

---

### Post by rick71 on 2009-03-05
bump

---

### Post by rick71 on 2009-03-18
If I understand the Homes share correctly,you don't access it like other shares. You access it by using either smb:/servername/username or \\servername\username, as opposed to accessing it by just clicking through the network/sambashares in the file manager.

If I am not correct, can someone please point me to some docs?

---

