---
title: "Ad hoc connected but cannot see other computer on network"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by GutiSteve on 2009-12-11
i created an ad hoc network to share files between my laptop and desktop.  both computers connect to the network just fine but when i go to places - network, the other computer is not listed.  

am i forgetting something?

---

### Post by adaucourt on 2009-12-11
> **GutiSteve said:**
> i created an ad hoc network to share files between my laptop and desktop.  both computers connect to the network just fine but when i go to places - network, the other computer is not listed.  

am i forgetting something?

what OS's?

---

### Post by GutiSteve on 2009-12-11
its ubuntu jaunty 9.04

both same OS

---

### Post by adaucourt on 2009-12-11
> **GutiSteve said:**
> its ubuntu jaunty 9.04

both same OS

can one computer ping the other? firewall?
make sure ports 32771, 111 and 2049 are open

see these links:
[http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/](http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/)
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)

this could be used as alternative:
[https://wiki.ubuntu.com/UbuntuOne/Tutorials/FileSharing#Share%20folders](https://wiki.ubuntu.com/UbuntuOne/Tutorials/FileSharing#Share%20folders)

---

### Post by GutiSteve on 2009-12-11
the ubuntu one link looks perfect for me.  althoug i tried installing according to these instructions...

[https://one.ubuntu.com/support/installation/](https://one.ubuntu.com/support/installation/)

and got this error

"could not find package ubuntuone-client-gnome

i searched synaptic and its not there.  does it show up in your synaptic?

---

### Post by adaucourt on 2009-12-17
> **GutiSteve said:**
> the ubuntu one link looks perfect for me.  althoug i tried installing according to these instructions...

[https://one.ubuntu.com/support/installation/](https://one.ubuntu.com/support/installation/)

and got this error

"could not find package ubuntuone-client-gnome

i searched synaptic and its not there.  does it show up in your synaptic?


sure does! ubuntuone-client and ubuntuone-client-gnome are both available and installed.  sorry it took so long to respond.

---

