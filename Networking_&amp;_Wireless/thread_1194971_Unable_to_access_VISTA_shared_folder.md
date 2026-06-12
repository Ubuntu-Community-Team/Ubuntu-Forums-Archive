---
title: "Unable to access VISTA shared folder"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by rmcder on 2009-06-23
I've searched some solutions to problems that sound like mine, but my attempts have so far been in vain.  Starting over, and looking for help...

I recently installed UBUNTU 9.04, having previously used version 7.10 (on a laptop connecting wirelessly).  I have a folder on my VISTA machine that is shared over my workgroup.  My username and password are the same on VISTA and UBUNTU.  7.10 was able to browse the shared folder, access files, etc.  With 9.04, I can see the workgroup and individual computers, and when I open the VISTA machine, I can see the various drives, including the shared folder (which is on the Z: drive, an external), but when I try to browse the shared folder, it asks for username, workgroup, and password.  Unlike 7.10, however, the same entries don't seem to work!  I've adjusted the smb.conf file to reflect the correct workgroup, and have identified my laptop with a unique name.  I've restored everything else in the file to its default settings.  My installation has only those components of samba that were installed by default.  Can someone maybe walk me through a solution?

---

### Post by dmizer on 2009-06-23
Please see the 6th link in my sig. If that doesn't fix your problem, read on. :)

Are you trying to share the entire drive from vista? Try sharing a single folder within the Z drive, and see if you can access that. If you make another share that's not in the Z drive, can you access that?

Do you have any firewalls on Vista?

---

### Post by rmcder on 2009-06-23
Thank you for the reply.  Problem boiled down to stupidity on my part, and your mention of drive versus folder led me to check what I was sharing, and it turned out that the folder I was trying to share wasn't being shared in the first place!  Not sure how that happened, but I reinstituted the share, and that, of course, fixed the problem.  Thanks again.

---

