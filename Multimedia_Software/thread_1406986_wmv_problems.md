---
title: "wmv problems"
date: 2010-02-14
forum: Multimedia Software
---

### Post by acornbrain on 2010-02-14
I can't seem to play .wmv files with movie player. (Jaunty) (I have restricted extras installed)

I tried installing some new movie software, like mplayer etc., but I keep getting this error:

E: Archive directory /var/cache/apt/archives/partial is missing.
E: Archive directory /var/cache/apt/archives/partial is missing.
E: Archive directory /var/cache/apt/archives/partial is missing.
E: Could not open lock file /var/cache/apt/archives/lock - open (5 Input/output error)
E: Unable to lock the download directory

I don't know what the error means. And if/when I correct the error, how do I view wmv files?

thank you, 

-brian

---

### Post by zeroseven0183 on 2010-02-15
Hi! Please use the LiveCD, boot from it and open a Terminal. Now, type:
```
cd /var/cache/apt/archives
```

You'll see there the .debs you used to install applications. Then run
```
sudo apt-get clean
```

You may check first what's in the archives folder by typing
```
ls
```

Type again ls after sudo apt-get clean and see if it deletes the files.

---

### Post by zeroseven0183 on 2010-02-15
By the way, don't forget to create first the partial folder with
```
mkdir /var/cache/apt/archives/partial
``` before running sudo apt-get clean

---

