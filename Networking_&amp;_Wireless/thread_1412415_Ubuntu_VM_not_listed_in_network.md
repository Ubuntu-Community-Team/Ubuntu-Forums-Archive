---
title: "Ubuntu VM not listed in network"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by eNc707 on 2010-02-21
Hi,

I installed a minimal ubuntu (minimal.iso) on a virtual machine (vmware) on my windows pc using following packages:
```
sudo apt-get install install gnome-core gdm network-manager-gnome human-theme x11-xserver-utils tangerine-icon-theme gnome-themes-ubuntu ubuntu-artwork jockey-gtk gnome-utils firefox
```I'm using the Ubuntu VM as my local http server. It is reachable via ip - so [http://IP-ADDRESS](http://IP-ADDRESS) works. I also use samba for shared folders... but ubuntu is not listed in my network. What means that i cannot access files from outside the vm. Do I have to install further packages, because "normal" ubuntu distributions are listed in my network connections.

Oh, I forgot to say, that the samba packages are correctly installed. ;)

Thx for Help. :)

(See [http://ubuntuforums.org/showthread.php?t=1410012](http://ubuntuforums.org/showthread.php?t=1410012) )

---

### Post by johnson.d on 2010-03-03
You can do the following checks:

1) Check whether the smb.conf file has the following condition in the relevant share section or in the global section:

browseable = yes

2) Use the command in the Samba server to list the shares present. This will tell you whether the Samba server is working fine and what shares are available.

$ sudo smbclient -L localhost

3) Try accessing the shares manually from terminal of the other Linux machines using the following command:

$ sudo mount -t cifs //<ip-address>/<share-name>/ /<mount-point>/ -o user=<user-id>

---

### Post by eNc707 on 2010-03-14
Thx,

It was the missing browsable field. :)

---

