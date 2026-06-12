---
title: "auto mount window share read/write problem"
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by halobend on 2011-01-03
OS=Ubuntu 10.10

I have 2 network drives on 2 different computers I'm trying to mount on startup. on the 2 windows computers within the share folders I have "users can change my files" checked. I have downloaded the smbfs files onto my ubuntu laptop. for one of the share drives the icon shows up on my desktop as though it has mounted but I don't have write access...not UNTIL I click on its network share type of icon under "places", after I do that a different "drive" icon shows up under "places". I can access the drive this way with read/write access...but anytime I click on the network share type of icon under "places" I get a unable to mount error that pops up telling me that it timed out, though I can still access it with the "drive" icon. Here is what my fstab line looks like...

//[ip adress]/[share folder] /media/[mymountfolder   smbfs] defaults,user,username=[myusername],password=[mypassword] 0 0
(entries in brackets aren't actually in brackets, I just didn't want to display those in this thread)


now on the second one I'm trying to auto mount on start up, no icon shows up on the desktop, and when I go to the actual folder where it is supposed to mount, the folder is empty as though it hasn't mounted yet. and just as the same above, it won't give me access to it until I click on the network share type of icon under "places" then the drive icon shows up and I can access and write to it. Here is it's line in fstab

//[ip adress]/[share folder] /media/[mymountfolder   smbfs] defaults,user,noauto,username=[myusername],password=[mypassword] 0 0

I understand the noauto, I was trying to see if it made any difference. another thing is that if I go to "places" and then click on "connect to server" and enter the information that way I can connect to them and also write to them. I just want to be able to do this at startup, but it's acting funny by making me click on the network icons in order to write to them.

Please help, I'm fairly new to the linux family...

halobend

---

