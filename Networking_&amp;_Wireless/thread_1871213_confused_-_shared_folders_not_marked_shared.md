---
title: "confused - shared folders not marked shared?"
date: 2011-10-28
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2011-10-28
Quite a while ago, I installed SAMBA and I shared a few folders over my network. I am pretty sure that I did it by right-clicking on the folder in Nautilus and selecting Share.

I just installed a new external harddrive and went to share it. I was told that I had to add the line "usershare owner only = false" to the smb.conf file, which I did, and the share worked fine. There are now two arrows superimposed on the folder icon in Nautilus showing that the folder is shared. The other folders that I have shared (and are still accessible across the network) do not have the arrows on their icons, nor is the Share box selected in their properties.

There are no entries in the smb.conf file associated with this shared folders, so my question is this: How are they being shared? If I were to want to unshare them, how would I do it, since they are not so obviously shared in the first place.

Thanks...

---

### Post by luvshines on 2011-10-28
To know if they are shared or not, you can use```
net usershare list
```
The shares which are shared by right-click nautilus option don't appear in smb.conf but would be visible in /var/lib/samba/usershares instead
To unshare them if they are shared, you can use command line options for "net usershare"

---

### Post by rebeltaz on 2011-10-28
That's what I was looking for! Odd that they don't have the "share" icon in Nautilus, but Thanks!

---

