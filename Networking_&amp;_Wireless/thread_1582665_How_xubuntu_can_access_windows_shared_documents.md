---
title: "How xubuntu can access windows shared documents"
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by Jinxzs on 2010-09-26
how i am so new with xubuntu i want to know how to set it up. im so new in xubuntu..

---

### Post by donc786 on 2010-09-28
Have you enabled the files in Windows for sharing? If not, that is the first step. The easiest way is to navigate to the folder, right click and enable sharing that way. If so, I would suggest installing smb4k and using it to manage the shared files. You can usually just scan the network with the program and select what you want to open. If that doesn't work, you'll have to press ctrl+o and mount the location by entering the IP and share. It would be in the format of something like //192.168.1.101/MUSIC You may need to enter a username and password if you enabled such requirements when you configured the share. This is how I was able to network with my Xubuntu notebook after several attempts at other methods.

---

### Post by pricetech on 2010-09-28
Install Samba on your Linux box.  system-config-samba should get you a GUI which will make it easier to configure.

---

### Post by Morbius1 on 2010-09-28
**[]** To access a windows shared folder:

Thunar doesn't have a built in Network browser so I would suggest Gigolo:

```
sudo apt-get install gigolo
```If I remember correctly it's missing a dependency so make sure the following is also installed:
```
sudo apt-get install gvfs-fuse
```Gigolo is a very impressive little application and with it you can browse, bookmark, and even mount at start-up a remote windows share.

**[]** To create a share for windows to access I would recommend a Thunar plugin:
```
sudo apt-get install thunar-shares-plugin
```With this you will be able to open Thunar > Right click a folder you own > Properties > Share ( just about the same way you'd create a share on WinXP )

---

### Post by Jinxzs on 2010-09-30
i will try this sir.s.. i will brb to post the outcome...thanks

---

