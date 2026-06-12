---
title: "Nvidia on Vaio, Again"
date: 2011-02-06
forum: Multimedia Software
---

### Post by klausner on 2011-02-06
I'm making my bimonthly attempt to get the nVidia drivers working on my Vaio VGN-Z530N. 

Using the Z-Series Janitor script, I get as far as 
   ```
 check version of the installed "sony-laptop" kernel module
     - installed version: "0.6"
     - available version: "0.9np7"
    There is a new version of the sony-laptop kernel module available. Upgrade?
    Make your choice: ([y]es or [n]o) [**yes**]: 

Error! DKMS tree already contains: sony-laptop-zseries-0.9np7
You cannot add the same module/version combo more than once.
```

I've searched the entire disk for instances of files with names containing "9np7". Where is this DKMS tree reference, and how do I fix it?

Tried some solutions I found here, like
```
sudo dpkg --configure --pending
sudo apt-get -f install
```

but no effect.

Is there a way to get nVidia running on Ubuntu? ](*,)

---

