---
title: "Nt_status_connection_refused"
date: 2011-01-01
forum: Networking &amp; Wireless
---

### Post by briangoldberg on 2011-01-01
I can't see my windows shares on ubuntu. ```
shoshana@ubuntu:~$ smbclient -L goldberg-pc -U Owner
Enter Owner's password: 
Connection to goldberg-pc failed (Error NT_STATUS_CONNECTION_REFUSED)

```
I also tried to go to connect to server. I choose Service Type windows share, server goldberg-pc, share users, folder public\pictures domain workgroup.

The error message I get is cannot display location "smb://workgroup; goldberg@goldberg-pc/users/public%5Cpictures"failed to mount windows share.

Then another dialog window message pops also with an error message.

DBus error.org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired or the network connection was broken.

---

### Post by PatchesTheCaveman on 2011-01-01
Are you connecting to a Windows 7 computer?  If so, check to see if Windows Live Essentials is installed.  The Windows Live Sign-In Assistant changes the way Windows communicates via SMB in fashion that breaks the version Samba included with Ubuntu.  While the Samba developers have fixed this bug, Canonical has not yet released an updated package for Ubuntu.

To work around this issue, uninstall Windows Live Essentials.  Please note that Microsoft sometimes installs this software as part of Windows Update, so you might not be aware you have it on your system.

---

### Post by briangoldberg on 2011-01-01
My computer called goldberg-pc is a windows vista computer.

Good news though my other computer is a windows xp computer and I had luck connecting to that one using the same procedure. Windows share, 
server= cpu, share =shareddocs, user =owner domain =mshome.

---

### Post by PatchesTheCaveman on 2011-01-02
I believe Windows Live Essentials is available on Windows Vista too (Windows 7 and Windows Vista aren't very dissimilar).  If you can connect to Windows XP its very likely you are experiencing this bug.

If not, check the settings in Network and Sharing Center and make sure file sharing is turned on.  You might have to change your connection to the network to "Home" or "Work" instead of "Public" if it is set to that as well.

---

### Post by briangoldberg on 2011-01-04
I dont think windows live essentials is installed. My network is set to private. Thanks for your help. file sharing is turned on.

---

