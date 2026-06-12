---
title: "fstab automount smb fails"
date: 2012-08-19
forum: Networking &amp; Wireless
---

### Post by jeremyjjbrown on 2012-08-19
I'm trying to automount some drives with smb with fstab entries as such.

```
# auto mount hda shares
//hda/DeannasDocs /home/deanna/DeannasServerDocs cifs user=deanna,pasword=** 0 0
//hda/Music       /home/deanna/ServerMusic        cifs user=deanna,pasword=** 0 0
//hda/Pictures    /home/deanna/ServerPhotos      cifs user=deanna,pasword=** 0 0
```

if I click on one of these drives I get an error "only root can mount"

If I manually mount with

```
sudo mount -a
```

I'm prompted for a password and they mount just fine. What the heck is going on here?

---

### Post by jeremyjjbrown on 2012-08-19
Of course it was something stupid.

I copied the syntax fro the mount from offline and it has "pasword" instead of "password". It stood out initially but I thought it was just a Unix foible.

---

