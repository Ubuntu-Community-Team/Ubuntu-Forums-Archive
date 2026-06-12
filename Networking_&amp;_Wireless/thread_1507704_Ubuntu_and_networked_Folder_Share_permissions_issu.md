---
title: "Ubuntu and networked Folder Share permissions issues."
date: 2010-06-11
forum: Networking &amp; Wireless
---

### Post by nssone on 2010-06-11
EDIT: I forgot to include the group id parameter (gid=) in fstab. After I included that, everything else fell into place.

Hey there guys. How y'all doing. As suggested, I'm currently having an issue with some shared folder from my Linksys NAS200 that I have not encountered before until recently after a fresh re-install of Ubuntu Karmic/Lucid. Some people I have talked to have suggested it could be a sharing/permissions problem on my NAS and I'm trying to make sure it's not to the best of my abilities.

Anyway, so here's my issue: I have 2 share folders I have mounted in my fstab as networked drives. This is what they look like in my fstab (with sensitive information omitted).
```
//192.168.1.149/music /home/tg37/Shared cifs rw,_netdev,user=user,password=password 0 0
//192.168.1.149/games /home/tg37/Games cifs rw,_netdev,user=user,password=password 0 0
```

I simply followed some guidelines on how to mount these from some search result i found while trying to remember how to do this again in the first place. This is how it laid it out as far as what to put in fstab to mount these drives. Now, the user I have assigned for these has full r/w permissions without admin controls set up on the NAS. Now I have 2 mounted network shared folders that only give me 501 level of permissions with all files and folders. 

And when I do get file writing access, I have an issue of files showing up both in the shared folder and in the folder on my hard drive (taking up precious space). I'm trying to make sure that anytime I select that folder it is only to access the shared folder on my NAS and not on my hard drive.

If anybody has any insight to this and knows of anything I would have to check that might be related to my NAS. Or if there's a better way to set up the folder sharing, feel free to enlighten me. 

Thank you for your time and for reading this.

---

