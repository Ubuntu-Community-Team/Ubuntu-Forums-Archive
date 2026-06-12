---
title: "Connect to DFS (distributed file system) on Win2K3 domain"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by timbertens on 2008-12-30
Hello,

I'm doing a trial to see if I can leave behind my Windows Vista completely in our business environment.  I'm almost there, but I cannot seem to find how to connect to our domain-based DFS 

Can anybody help?

thx,
Tim.

---

### Post by Metabaron on 2009-05-11
I have the same problem when I run nautilus with gvfs/smb. smbclient does handle this. 
Currently we run "smbclient -k '//domain.net/mynet/share' -c list" too resolve the "real" path.

BR
Emil Assarsson

---

### Post by timur_ba on 2009-09-08
I posted a similar question on [https://answers.launchpad.net/ubuntu/+question/17802](https://answers.launchpad.net/ubuntu/+question/17802)

If there is a DFS created in Windows Server \\DomanName\Share, how can it be open from Linux client?
AFAIK, I can open only smb://ServerName/Share/.
Is there any way or DFS client in Linux to open \\DomanName\Share in GUI, such as Nautilus?

---

### Post by timur_ba on 2009-09-08
I posted a similar question on [https://answers.launchpad.net/ubuntu/+question/17802](https://answers.launchpad.net/ubuntu/+question/17802)

If there is a DFS created in Windows Server \\DomanName\Share, how can it be open from Linux client?
AFAIK, I can open smb://ServerName/Share/ where ServerName is DFS root and not real file server. 
Is there any way or DFS client in Linux to open \\DomanName\Share in GUI, such as Nautilus?

---

### Post by mr_skater99 on 2009-10-06
I have the same problem - yet the guy beside me running Fedora 11, this works out of the box!

---

### Post by theharveyman on 2012-01-04
I know this is an old thread, but it took me a while to find the answer to this myself so I thought I'd share it here.  Check out this nice write-up, especially the info near the bottom:
 
[http://webscript.princeton.edu/~pug/faqwiki/index.php?title=Using_SAMBA/CIFS_to_access_Windows_Shares](http://webscript.princeton.edu/~pug/faqwiki/index.php?title=Using_SAMBA/CIFS_to_access_Windows_Shares)
 
Cheers

---

