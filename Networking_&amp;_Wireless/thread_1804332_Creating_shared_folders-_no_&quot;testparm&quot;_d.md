---
title: "Creating shared folders- no &quot;testparm&quot; directory"
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by varelov on 2011-07-14
I need to share some files from my Ubuntu 10.10 box to others on my home network so I created a shared folder, right-clicked it and chose "Sharing Options", chose "Share This Folder" and then I was told that additional software is needed to enable sharing. I agreed and software was downloaded and installed. But when I clicked "Create Share" button and told Nautilus to automatically add permissions for others to access my folder, I was slapped with an error message saying "Failed to execute child process "testparm" (no such file or directory).
So how to proceed and get sharing working again? I installed Samba afterwards via Synaptic and assigned the folder for sharing, but I don't see the special "arrows-both-ways" sign for this folder.

---

### Post by Morbius1 on 2011-07-14
Go into Synaptic and see if the following package is installed:
```
samba-common-bin
```If it is installed reinstall it.

You may need to restart the samba service after that:
```
sudo service smbd restart
```

---

### Post by varelov on 2011-07-14
Thank you Morbius1, that and some other packages needed an update and after that it worked.

---

