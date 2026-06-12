---
title: "Cannot Connect to NAS"
date: 2013-08-03
forum: Networking &amp; Wireless
---

### Post by rbscairns on 2013-08-03
I have an NTFS formatted HDD connected via USB to my wireless router (running DD-WRT) that I use as a basic NAS on my wireless network. My network includes 2 x Win XP computers and a Ubuntu 12.04 computer.

I recently had to reinstall my Ubuntu 12.04. Since then, I am unable to connect to my NAS. Here is what I do:
[LIST=1]
[*]Click on Places>Network
[*]This opens a window that displays an icon for "Windows Network".
[*]I click on the "Windows Network" icon and get the message "**Unable to mount location** - Failed to retrieve share list from server".
[/LIST]
I have checked my /etc/samba/smb.conf file and "workgroup = NSD" which is correct.

My router does not have MAC filtering enabled nor does it have any other access restrictions set for the NAS HDD. The Win XP computers have no problem accessing the NAS HDD.

How can I access my NAS on my Ubuntu computer?

---

### Post by rbscairns on 2013-08-03
I spent hours researching and trying various methods to solve this problem. I eventually found the solution!

The solution that worked for me was to delete Ubuntu 12.04 and reinstall it. It only took me a few hours, but I had spent twice as long researching and trying other suggested solutions.

---

