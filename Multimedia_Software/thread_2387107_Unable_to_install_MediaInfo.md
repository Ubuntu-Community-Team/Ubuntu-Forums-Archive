---
title: "Unable to install MediaInfo"
date: 2018-03-14
forum: Multimedia Software
---

### Post by wrongusername2 on 2018-03-14
I am trying to install MediaInfo with no success. deb installation complained about libzen0v5, libzen0 packages. I added those packages, and PPA, still no success. Please help me resolve this




Installed deb files
```
   dpkg -i libmediainfo0v5_17.12-1_amd64.xUbuntu_16.04.deb
   dpkg -i mediainfo-gui_17.12-1_amd64.xUbuntu_16.04.deb
 
   dpkg: dependency problems prevent configuration of libmediainfo0v5:amd64:
     libmediainfo0v5:amd64 depends on libmms0 (>= 0.4); however:
    Package libmms0 is not installed.
    libmediainfo0v5:amd64 depends on libzen0v5 (>= 0.4.37); however:
     Package libzen0v5 is not installed.

```






Installed packages
```
sudo apt-get install libmms0
   Package libmms0 is not available, but is referred to by another package
   E: Package 'libmms0' has no installation candidate

```




Installed PPA
```
sudo add-apt-repository ppa:mediainfo/ppa
            sudo apt-get update
W: The repository 'http://ppa.launchpad.net/mediainfo/ppa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://ppa.launchpad.net/mediainfo/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

```


I thought adding PPA would solve the problem but it did not.

---

### Post by wrongusername2 on 2018-03-14
This resolved it
            	sudo add-apt-repository universe

---

