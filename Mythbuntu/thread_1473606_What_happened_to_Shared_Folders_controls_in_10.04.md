---
title: "What happened to Shared Folders controls in 10.04?"
date: 2010-05-05
forum: Mythbuntu
---

### Post by neutron68 on 2010-05-05
I've been using the SAMBA Shared Folders function to allow other pcs in my home network to pull video files off the Mythbuntu machine.

After the upgrade from 9.10 to 10.04, the Shared Folders controls are gone, and when I log into the Mythbuntu machine from another pc, I can see the shared folders, but I can't have access to the files.

What happened?  It appears SAMBA has been broken by the upgrade.

Help appreciated,
Eric

---

### Post by emillan on 2010-05-05
I did a fresh install, so I can't speak to the problem of your existing Samba shares, but when I noticed that the Shared Folders functionality was removed, I installed system-config-samba to create my shares.  It's easy to use and works very well.  Perhaps it can help you.

Emilio

---

### Post by neutron68 on 2010-05-05
Thanks for the suggestion.  I went into Synaptic Package Manager and added the package you mentioned.  I've got the controls back.  

I wonder why that package was left out of the new release?  
The developers forgot and none of the testers noticed?

Eric

---

### Post by neutron68 on 2010-05-05
I just tried to access files in the shared folders from another computer - nope.  SAMBA will not let me.

I believe there was a "security update" about 1 month ago to SAMBA.  This may be the culprit.

Eric

---

### Post by neutron68 on 2010-05-05
I found it.  It is a problem with symlinks.

see [http://ubuntuforums.org/showthread.php?t=1439092](http://ubuntuforums.org/showthread.php?t=1439092)

To undo the "fix", you have to edit the /etc/samba/smb.conf file.
In the [global] section, set "wide links = yes", and restart SAMBA (sudo service smbd restart)

Then, you can access symlinks through the SAMBA interface again.
 
Eric

---

