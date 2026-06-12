---
title: "No videos in Mythtv unless in default directory"
date: 2011-01-04
forum: Mythbuntu
---

### Post by Michaelknox on 2011-01-04
I have 2 other drives with movies and I placed the paths into the storage directories at Mythtv and even placed links inside the default directory pointing to the 2 folders but it says no movies... when I place a movie in the default directory it works fine. Thanks

---

### Post by tgm4883 on 2011-01-04
Likely permissions issues, please post the permissions of the directory you placed the files in and all directories above it in the tree.

---

### Post by Michaelknox on 2011-01-04
the directory is /media/Storage/Mythtv/Video the permissions are
drwxrwxrwx and mythtv is the owner...thanks
 
for Storage is drwx------ 
for Mythtv is drwxr-xr-x

---

### Post by tgm4883 on 2011-01-04
> **Michaelknox said:**
> the directory is /media/Storage/Mythtv/Video the permissions are
drwxrwxrwx and mythtv is the owner...thanks
 
for Storage is drwx------ 
for Mythtv is drwxr-xr-x

your Storage directory is incorrect. It either needs to have read and execute permissions for everyone, or be owned by the mythtv group (not user) and have group permissions of read and execute.

---

### Post by Michaelknox on 2011-01-04
Thank you so much

---

