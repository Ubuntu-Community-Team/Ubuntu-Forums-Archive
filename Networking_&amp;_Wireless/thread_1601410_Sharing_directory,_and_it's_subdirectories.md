---
title: "Sharing directory, and it's subdirectories"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by Oxwivi on 2010-10-20
I've been doing some file-sharing with Ubuntu. And I've noticed that the files only in the immediate directory is shared, the rest of the folders are shown in other PCs but access is denied. How can I share all the subdirectories in a folder without having to them manually?

---

### Post by luvshines on 2010-10-20
Did you check the permissions on the subdirectories, are they readable/executable ?

---

### Post by Oxwivi on 2010-10-20
I had just copied some content from an USB. Other then owner, the permissions for Folder access is Access files.

---

### Post by glacian79 on 2010-12-09
Having exactly the same problem.  What is going on?  Expected this to be so simple.

---

### Post by luvshines on 2010-12-11
Again the same question :)
Can you paste output of following:
```

testparm -s

# You may hide the file/directory names if you like, just want to check the permissions
ls -l <shared-directory>
```

---

### Post by Oxwivi on 2010-12-12
I've given up on it.

---

### Post by calvin mitchell on 2011-01-23
I had the same problem.  Here's what worked for me:

1. Share the desired directory - right click relevant directory > Sharing Options > check "Share this folder"

2. Apply settings to subdirectories - right click same directory > Properties > select "Permissions" tab > select "Apply Permissions to Enclosed Files"

Hope that helps.

---

