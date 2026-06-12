---
title: "Installing a package from CD"
date: 2009-10-17
forum: Networking &amp; Wireless
---

### Post by Deverell on 2009-10-17
Hello, 

I need help trying to install network-manager without the internet. 
Steps I have taken:

```
sudo apt-cdrom add
sudo apt-get install network-manager-gnome
```

However apt-get still tries to use online sources and fails. I assumed that simply adding the CD-ROM (My Jaunty Install) as a source would resolve this since apt-get would move to a secondary source once the online ones proved inaccessible. 

Thanks, 
Deverell.

---

### Post by Deverell on 2009-10-17
I'm sorry to see this thread got no replies. 

Anyway for future Googlers, I found a solution. 

[LIST=1]
[*]Using another computer download the following packages:
[network-manager-gnome]("http://packages.ubuntu.com/jaunty/i386/network-manager-gnome/download")
[network-manager]("http://packages.ubuntu.com/jaunty/i386/network-manager/download")
[*]Transfer the files to the broken computer and double click. Your distribution should recognize them as packages and open an appropriate package manager. Make sure no other package managers are open or running otherwise an error will occur. 
[*]Open a terminal and provide the following command:
```
sudo /etc/init.d/NetworkManager start
```[/LIST]

---

