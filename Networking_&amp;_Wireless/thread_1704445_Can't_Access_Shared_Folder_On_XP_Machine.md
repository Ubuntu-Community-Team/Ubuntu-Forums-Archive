---
title: "Can't Access Shared Folder On XP Machine"
date: 2011-03-10
forum: Networking &amp; Wireless
---

### Post by golfnut324 on 2011-03-10
Hi everyone! Been using Ubuntu now almost 1 year and love it but I'm still mostly lost so I need someone to explain in great detail how to be able to access the My Documents folder on my LAN XP machine. I've been up and working fine for 6 or 8 months but all of the sudden (maybe it was an update package?) I get the following error message, after a long delay, when trying to access the shared folder:

Could not open location 'smb://office/my%20documents/'
Failed to mount Windows share

I have set an icon on the top panel mapped to the XP machine and launched by launcher.

Ubuntu 10.04

Hope that's enough info and thanks for the time and help.

Craig

---

### Post by golfnut324 on 2011-03-15
Bump.

---

### Post by ant2ne on 2011-03-15
Too much to troubleshoot...

From the connecting machine: can you ping office by name? if not, can you ping office by IP?

is the share on office still being shared? what are the permissions on it?

I haven't much faith in the gnome GUI samba mount utility. For me, it keeps forgetting (or corrupting the bookmarks or locations) Have you tried used the command line? You could also try reconnecting to the share by clicking on "places" and then "connect to server" and then filling out all of that information again.

---

### Post by golfnut324 on 2011-03-23
Sorry it took me so long to respond and thanks for the help. I could not ping "office" but could ping the ip so I changed the location on the launcher properties dialogue to the ip and it works now.

I surely don't understand networking stuff but I do like to be able to manage files from my ubuntu machine.

Thanks for the tips.

Craig

---

### Post by ant2ne on 2011-03-24
Name resolution in a windows work group is flaky. In a work group it is best to use IP addresses.

---

