---
title: "Error when editing/saving an XP file from Karmic Using gedit"
date: 2010-01-02
forum: Networking &amp; Wireless
---

### Post by wdavro on 2010-01-02
I have a new install of Karmic (not an upgrade) on my home network.  All the other machines are XP sp2 or sp3.  I have the following line in /etc/fstab:
```
//desktop/ddrive     /home/dram/aDesktop-D          cifs credentials=/etc/credentials.dt,nobrl,uid=1001,gid=1001 0 0 
```
Where; desktop is an XP sp2 system; /home/dram is my Karmic home folder; 1001 is my Karmic uid and gid.

I can copy files just fine from one to the other.  however, if I open gedit on the Karmic system and then have gedit edit a file on the XP system, when I save the changes I get a red box at the top of the gedit window that says:
```
Could not find the file /home/dram/aDesktop-D/TEST.TXT.
Please check that you typed the location correctly and try again.
```
But in fact, a backup file has been created and the file changes have been saved to the original file.

Though I'm very new to Ubuntu, I don't remember having this problem when I was on Jaunty for the couple months I had it (the Seagate 1TB drive failed after 2 months, so I got a new one and installed Karmic instead of Jaunty).

Is this expected behavior for Karmic?  Or have I got something configured incorrectly?

Thanks,

---

### Post by falconindy on 2010-01-03
What happens if you use the IP instead of the netBIOS name in the fstab entry?

---

### Post by dc45 on 2010-02-03
I too am having the exact same problem.  I tried mounting using the IP address instead of the hostname as suggested by falconindy and am still receiving the same error.  Any other ideas?

---

