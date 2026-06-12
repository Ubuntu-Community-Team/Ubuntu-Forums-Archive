---
title: "Amarok duplicates collection"
date: 2009-01-05
forum: Multimedia Software
---

### Post by gotanothergrot on 2009-01-05
Help 

When i open amarok it begins updating my collection, nothing wrong with this accept what its doing is Duplicating everything in my collection, any help to fix it would be greatly appreciated.

Also when i try the help tab for the amarok handbook i have  

'could not launch the KDE help center, could not find the service 'Khelpcenter' what should i do.


Thanks

---

### Post by Elfy on 2009-01-07
I would first check how you have collection set up in the settings. 

You can regenerate the database by removing it and restarting amarok - the file should be in ~/.kde/share/apps/amarok/

You can move it to the Desktop and delete it later once the problem is solved

```
mv ~/.kde/share/apps/amarok/collection.db ~/Desktop/collection.db
```

Restart amarok and it will rebuild the dbase.

To get the KDE help centre

```
sudo apt-get install khelpcenter
```

---

