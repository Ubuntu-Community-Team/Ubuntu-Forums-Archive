---
title: "Need Help Getting Write Privileges To Network Shares on NAS Storage Device"
date: 2013-08-25
forum: Networking &amp; Wireless
---

### Post by shalamigri on 2013-08-25
I have a Netgear ReadyNAS Ultra 4 server that I can access perfectly fine by using the File Manager in Ubuntu 13.04. Many of the share folders on my NAS device have read only access by default so accessing them in Ubuntu is not a problem at all. I also have shares on my NAS that are disabled for viewing by default and the Ubuntu File Manager will prompt me to enter a username and password to access those shares. So far, so good.

My problem is that I can't seem to figure out how I can enter a username and password for shares that have read only access by default. I'd like to be able to get write privileges to those shares so that I can copy files to them from Ubuntu.

Again, I can access files and folders from the read only shares just fine. I can also copy files and folders to shares that are disabled by default as well after successfully logging into any share that is disabled by default. I just want to know how to enter a username and password for an account that's stored on the NAS to get write privileges to my read only shares because I keeping a "read only" error when trying to create or copy a file to a read only share.

---

### Post by shalamigri on 2013-08-26
I got it to work.

Here is my scenario explained a little better. I have about 10 shares on my NAS device of which 4 are read only by default and 6 are disabled by default. When using the file manager in Ubbuntu and browsing to my detected network storage device, I am prompted with a screen to enter a username and password when trying to access any disabled share. After entering a username and password that has write privileges to ALL of my shares on my NAS, I can successfully read and write to all disabled shares, but not the read only shares. I was assuming that I'd also be able to write to my read only shares after doing this because this is how it works when using Windows 7 and 8.

I didn't think I'd have to do this, but I ended up editing my etc/fstab file to get write privileges for my read only shares.

---

