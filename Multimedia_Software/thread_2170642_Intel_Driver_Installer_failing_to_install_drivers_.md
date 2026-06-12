---
title: "Intel Driver Installer failing to install drivers on Ubuntu 13.04"
date: 2013-08-27
forum: Multimedia Software
---

### Post by steaksoldier on 2013-08-27
I am trying to install Intel graphics drivers on my Gateway NV57H laptop using the Intel Driver Manager and I keep getting this message:

W:GPG error: [https://download.01.org](https://download.01.org) Ubuntu Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8D8847D52F4AAA66, W:Failed to fetch [http://ppa.launchpad.net/ehoover/compholio/ubuntu/dists/raring/Release.gpg](http://ppa.launchpad.net/ehoover/compholio/ubuntu/dists/raring/Release.gpg)  Something wicked happened resolving 'ppa.launchpad.net:http' (-11 - System error)
, W:Failed to fetch [http://ppa.launchpad.net/tspindler/ppa/ubuntu/dists/raring/main/source/Sources](http://ppa.launchpad.net/tspindler/ppa/ubuntu/dists/raring/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/tspindler/ppa/ubuntu/dists/raring/main/binary-amd64/Packages](http://ppa.launchpad.net/tspindler/ppa/ubuntu/dists/raring/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/tspindler/ppa/ubuntu/dists/raring/main/binary-i386/Packages](http://ppa.launchpad.net/tspindler/ppa/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I am not sure if it is problem with my hardware or if 13.04 is not supported for my drivers any help is appreciated.

---

### Post by deadflowr on 2013-08-27
First off, all Intel linux drivers are open source and included in default drivers on Ubuntu.
So, unless you've got the absolute latest in Intel hardware, you shouldn't need to install drivers.

Secondly, The PPA for tspindler has seemingly not been maintained or added to for five(5) years.
The last supported version of Ubuntu for that PPA was hardy/8.04.

It's best to open up software and updates, go to 'other software' and find the listings for that ppa and disable/remove.

---

### Post by Yellow Pasque on 2013-08-27
The NV57H looks like an Optimus (hybrid Intel/Nvidia graphics) system. See: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by Bucky Ball on 2013-08-27
*Thread moved to **Multimedia & Video**.*

Welcome to the forums. You might have better luck here.

---

### Post by wildmanne39 on 2013-08-27
None of these [http://ppa.launchpad.net/tspindler/ppa/ubuntu/dists/raring/main/source/Sources](http://ppa.launchpad.net/tspindler/ppa/ubuntu/dists/raring/main/source/Sources) are on the servers any more that is why you can not download them, best to remove as stated in the deadflowr.

---

