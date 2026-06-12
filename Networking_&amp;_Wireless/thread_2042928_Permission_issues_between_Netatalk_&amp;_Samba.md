---
title: "Permission issues between Netatalk &amp; Samba?"
date: 2012-08-15
forum: Networking &amp; Wireless
---

### Post by putz3000 on 2012-08-15
I am currently trying to roll out a 10.04 LTS server install with Netatalk & SAMBA installed. My current Netatalk install is version 2.0.5-3 according to the "dpkg -l netatalk" command.  I am aware of at least two significant updates to Netatalk that I am currently looking into applying. However, I have a problem that I am not sure is related to the version.

Here is my current issue:

Mac users can delete anything and everything they want. PC users are unable to actually delete folders that Mac users created. What is interesting is that if you try to delete a folder from the PC (Mac created) and that folder has content inside of it, the content will be deleted but not the folder. I have only tested that on files stored inside the folder to date. I am "assuming" that nested folders would not be removed but have not tested it.

I just checked the "/data" folder which holds the "/editorial" folder has the following permissions (ls -l /data):

drwx---rwx => so all other users have read, write and execute permissions.

The nested editorial folder however gives me the following error when I try to check it specifically:

ls: cannot access /editorial: No such file or directory

If I execute the command but leave off the "/" from in front of editorial it shows me the contents which strangely do not all have the same permissions.

---

