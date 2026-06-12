---
title: "erros as i try to update linux mint 19.3"
date: 2020-04-16
forum: MINT
---

### Post by bponanza on 2020-04-16
```
bonanza@bonanza:~$ sudo apt update
Ign:1 [http://packages.linuxmint.com](http://packages.linuxmint.com) tricia InRelease                           
Hit:3 [http://packages.linuxmint.com](http://packages.linuxmint.com) tricia Release                             
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [88.7 kB]    
Err:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease                        
  Connection failed [IP: 2001:67c:1562::15 80]
Get:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease [46.9 kB]           
Err:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease                     
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates InRelease [46.9 kB]      
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports InRelease [46.9 kB]
Err:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Err:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Reading package lists... Done       
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
E: The repository 'http://archive.canonical.com/ubuntu bionic InRelease' is no longer signed.
E: Failed to fetch [http://archive.canonical.com/ubuntu/dists/bionic/InRelease](http://archive.canonical.com/ubuntu/dists/bionic/InRelease)  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease)  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: The repository 'http://archive.ubuntu.com/ubuntu bionic-updates InRelease' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease](http://archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease)  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: The repository 'http://archive.ubuntu.com/ubuntu bionic-backports InRelease' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

---

### Post by jeremy31 on 2020-04-16
Moved to Mint

---

