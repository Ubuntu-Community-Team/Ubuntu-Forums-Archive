---
title: "Mythbuntu &quot;Add to Ubuntu&quot; failed. What next?"
date: 2010-01-07
forum: Mythbuntu
---

### Post by BFG on 2010-01-07
I'm new to Mythtv.

I found the Mythbuntu download here:
[http://www.mythbuntu.org/download-type](http://www.mythbuntu.org/download-type)

No install docs on the site, but I tried anyway.
Clicked "Add to Existing Ubuntu Install"

This tried to automatically launch an installer.  Hmm. Bit like microsoft ;).  It failed. Firefox didn't know what to do with the file.  
Chrome did though, so off I went.

It failed because of no permission to create /home/mythtv
I was worried about that assumption.  I mount /home from a NAS using autoFS, so nothing is going to be able make new directories there.
I closed the window.

OK, so off I go to the server, and create a folder called mythtv in the share will 777 permissions.
Click the download again, run the installer.
"Package 'mythbuntu-control-centre' is already installed".  And it would go no further. There's that windows feeling again ;) ;)

How can I unravel this, and work out what is installed, and what is yet to be installed?  There's no mythtv in the menus.

---

