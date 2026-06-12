---
title: "[SOLVED] Share F-Spot db between 2 users?"
date: 2008-02-14
forum: Multimedia &amp; Video
---

### Post by LilYoda on 2008-02-14
Is it possible to share the fspot database between 2 users?  My wife has her own account and I'd like her to be able to import pics from the digital camera, and for me to be able to tag them later?

---

### Post by olejorgen on 2008-02-14
As long as you don't use fspot simultatiously it should be no problem. I'd suggest creating a group called shared_fspot or something and add both you and your wife to it. 
Decide where you want to store the database. I will refer to this location as DBPATH.
As the user currently having the fspot database:
```

cp ~/.gnome2/f-spot/photos.db DBPATH
chgrp shared_fspot DBPATH
chmod g+rw DBPATH
mv ~/.gnome2/f-spot/photos.db ~/.gnome2/f-spot/photos.db.backup
ln DBPATH ~/.gnome2/f-spot/photos.db 

```
As the other user
```

mv ~/.gnome2/f-spot/photos.db ~/.gnome2/f-spot/photos.db.backup
ln DBPATH ~/.gnome2/f-spot/photos.db

```

Should do the trick. It might be possible to instruct f-spot directly to use a spesific .db file too

---

### Post by LilYoda on 2008-02-15
It works...  Had to change the link to a symbolic one, since I stored the photos.db file on a NFS share, where the photo files are.

Thanks

---

### Post by njbair on 2008-06-25
My wife asked for the same thing. I left photos.db alone under my user account and ran chgrp and chmod as shown. I also had to change permissions on ~/Photos/ (obviously recursively). I set up my wife's account with a hard link to photos.db and a symlink to ~/Photos/.

Now the files all exist physically under my home directory, and my wife's user account links to them. This is all that is necessary for two (or more) users on a single HD.

---

