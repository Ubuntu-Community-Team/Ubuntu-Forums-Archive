---
title: "Unable to access Windows network folders"
date: 2012-03-08
forum: Networking &amp; Wireless
---

### Post by qbektrix on 2012-03-08
I just downloaded and tried Xubuntu 11.10. Its a beauty but one major problem.

I an unable to access the windows network folders. I tried pyneoghbourhood, samba, Gigolos, Smb2k. When I googled, i found that issue is been around since 2007. I just could not fix the issue.

Why is this a problem? Did I oversee something obvious? Ubuntu & Knoppix had no issue, why is this a problem with Xubuntu?

Pls give me help in simple english. Despite toying with linux for a while, I am still a hardcore windows user. Have trouble writing scripts and playing around terminal.Pls be gentle.

---

### Post by Toz on 2012-03-14
Look for and install **gvfs-backends** from the software centre (you may have to log out and back in again afterwards, not sure). Startup Thunar (the file manager) and you should now see a Network option. Have a look there to see if you can get access to your windows network folders.

---

