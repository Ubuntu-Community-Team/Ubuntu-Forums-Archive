---
title: "How to download Audacity 1.2.6"
date: 2009-06-11
forum: Multimedia Software
---

### Post by tomreid on 2009-06-11
Hi

The version of Audacity available in the software repositories in Ubuntu is 1.3.7 which the Audacity web site says is a beta build. Is has been crashing and freezing a lot on my system, so i wondered if anyone knows how to download a .deb file of the previous stable release (1.2.6). 

For some reason only 1.3.7 is available in the Ubuntu repositories, i have download a tar gz file of the source code of 1.3.7., but compiling software is something I've yet how to learn how to do.

Thanks

---

### Post by shiggydiggy on 2009-08-22
i'm looking for this aswell! Help!

---

### Post by Copernicus1234 on 2009-08-22
Compiling should be easy if its a standard package. Just unpack, go to the directory, type *./configure* and let it configure itself. Then type *make*, and when its done building, you can install with *sudo make install*.

If you install it this way however, it may conflict with existing versions so I would remove the old synaptic package first. And if you want to uninstall this later, you need to type *locate audicity* and manually remove all the files. Packages are easier for a reason. :)

---

### Post by gjoellee on 2009-08-22
Download the tarball: [http://audacity.googlecode.com/files/audacity-src-1.2.6.tar.gz](http://audacity.googlecode.com/files/audacity-src-1.2.6.tar.gz)
Extract it, then as it says in the README you install audacity with the following commands:
```
./configure
  make
  sudo make install
```

of course you have to navigate to the audacity folder. That can be done with:

```
cd /home/$user/path/to/your/audacity/folder
```

you probable won't have to remove the "/home/$user/" has $user goes to the home folder for the user you are currently using.

---

### Post by shiggydiggy on 2009-08-22
how do i get all the dependecies needed to compile it?

---

### Post by magicmax0 on 2009-08-22
All you need is "audacity" and "audacity-data". You can also try the newer 1.3.8 version, you can get the .deb files [here]("http://www.getdeb.net/search.php?keywords=audacity"). Just download both packages and double click to install them, they can be deleted after install.

---

### Post by shiggydiggy on 2009-08-22
> **magicmax0 said:**
> All you need is "audacity" and "audacity-data". You can also try the newer 1.3.8 version, you can get the .deb files [here]("http://www.getdeb.net/search.php?keywords=audacity"). Just download both packages and double click to install them, they can be deleted after install.
How do i install them? they both *depend* on each other to install..

---

### Post by shiggydiggy on 2009-08-22
how do you install packages that depend on each other?

---

