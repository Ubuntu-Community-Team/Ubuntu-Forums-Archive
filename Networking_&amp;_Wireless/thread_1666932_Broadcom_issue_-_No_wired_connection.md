---
title: "Broadcom issue - No wired connection"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by nintendo on 2011-01-14
Hi all,

I just installed 10.10 on my laptop alongside windows 7. The thing is that I'm travelling in Europe right now and the only possible connection I have to the internet is by WiFi. I can't update synaptic package manager using wired connection. I was wondering if there's a way to download the necessary files on windows and then just install them on Ubuntu. I've tried downloading [_this package_]("http://pkgs.org/ubuntu-10.10/ubuntu-multiverse-i386/broadcom-sta-common_5.60.48.36-2_all.deb.html") but it doesn't solve the problem.

Thank you for any help :)

---

### Post by dineshs on 2011-01-14
I do not know whether there are easier methods but...
1)Open synaptic package manager-rightclick the package and mark it for installation (do not apply)
2)Go to file-Generate package download script-save it in your home folder
3)Open the file and note down the packages required.For example if the first line reads```
wget -c http://tf.archive.ubuntu.com/ubuntu/pool/universe/2/2vcard/2vcard_0.5-3_all.deb
```the package is 2vcard_0.5-3_all.deb
4)Download all files via windows.Store it in a thumb drive.
5)Run (ubuntu machine) ```
gksudo nautilus /var/cache/apt/archives
```
Copy and paste all the downloaded files to /var/cache/apt/archives
6)Finally open synaptic package manager-rightclick the package again and mark it for installation - apply
Let us wait for other solutions

---

### Post by nintendo on 2011-01-15
thanks for your help

unfortunately since I can't get to update the database for the available packages I don't know which packages to install.

I'll look around the forums to see if I cant get the names of the packages needed and install them using your method. Thank you!

---

