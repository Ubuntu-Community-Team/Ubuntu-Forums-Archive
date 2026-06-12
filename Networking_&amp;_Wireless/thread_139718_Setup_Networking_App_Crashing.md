---
title: "Setup Networking App Crashing"
date: 2006-03-04
forum: Networking &amp; Wireless
---

### Post by Maverick88 on 2006-03-04
just installed Breezy Badger. Since I use wireless encrypted networking, Breezy Badger was not able to properly setup my networking during installation.

I have rebooted into the GNOME desktop. I tried SYSTEM - ADMINISTRATION - NETWORKING, but the networking app just dies after I enter my password. (It makes no difference if I enter my User password or my root password). I see the whell turning and the "Starting Networking" in the taskbar, but then it just disappears. Strange.

I was able to get wireless networking up and running using iwconfig and dhclient at the command prompt.  But the GUI network app still crashes.

How can I fix this?  
Do I need to reinstall Breezy Badger?

Rob

---

### Post by Maverick88 on 2006-03-04
I think I found a solution.  

Apparently, when you use the "expert" mode during installation, the sudoer file is NOT properly created.  

See [http://www.ubuntuforums.org/showthread.php?t=132744&highlight=sudoer](http://www.ubuntuforums.org/showthread.php?t=132744&highlight=sudoer)

I added the line:

                harry   ALL=(ALL) ALL

Now I can set up networking with the System - Administration - Networking GUI app.  

But did I give my user harry to many privileges?  
What does Breezy normally setup  in the sudoers file?

It would be greatly appreciated if someone could open /etc/sudoers and let me know what is typically in the file.  If you could post the file that would be great.

Rob

---

