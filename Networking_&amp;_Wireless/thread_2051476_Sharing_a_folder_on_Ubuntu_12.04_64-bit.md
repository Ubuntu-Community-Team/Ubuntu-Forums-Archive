---
title: "Sharing a folder on Ubuntu 12.04 64-bit"
date: 2012-09-01
forum: Networking &amp; Wireless
---

### Post by 10mupload on 2012-09-01
I have tried two ways for sharing a folder on Ubuntu 12.04 64-bit so that I could access it on a Windows XP PC on the same switch:

1st: right-clicking the folder > properties > share > Share this folder and checking both "Allow others to create and delete files in this folder" and "Guest access (for people without a user account)"

2nd: adding the folder to Samba Server Configuration checking both "Writable" and "Visible" options under "Basic" and selecting "Allow access to everyone" under "Access".

But I was not successful because in both cases I received the following error message when trying to open the shared folder from the PC with Windows XP:

==

sf server (Samba, Ubuntu) (Sf)

\\Sf\shared mb is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions. Access is denied.

OK

==

I made sure the two PC are in the same workgroup. Could you please help me figure out why this is happening and how to fix it?

Thank you for your time!

---

