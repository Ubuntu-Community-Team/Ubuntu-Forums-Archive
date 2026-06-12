---
title: "Samba share only available when root &lt;10.04&gt;"
date: 2010-07-08
forum: Networking &amp; Wireless
---

### Post by Gaztech on 2010-07-08
Hello,

I've tried setting up a share on my desktop PC so that my laptop can view files present on the desktop, the files are located on an NTFS formatted drive which I also use with Win7 which I have dual booted. 

Using the "Share" option on the right click menu I highlighted the folder I wanted to share and I got the "Ubuntu needs to install sharing software" prompt so off it went and downloaded some packages. 

Once these had completed I was met with a message stating I do not have permission to share the folders as they are owned by Root. So I launched nautilus with "gksudo nautilus" and attempted to change the owner of the folder. Oddly it wouldn't let me, from the properties menu I selected the Owners tab and attempted to change the owner of the folder from Root to me but after I had clicked my username the drop down box in the properties menu would flick back to saying it was owned by Root :(

Curiosity got the better of me at this point and I attempted to share the folder as Root which worked! However when I closed the nautilus window I was running as root, the folders were unshared. running another nautilus session as root would re-enable the shares. 

Can someone help me either a) change the owner of the share to my user and not root or b) offer any insight as to why I cant change the permissions of a folder on an NTFS drive to be owned by me rather than root?

Thanks in advance for any help.

---

