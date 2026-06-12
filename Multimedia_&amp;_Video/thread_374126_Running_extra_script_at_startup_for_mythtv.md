---
title: "Running extra script at startup for mythtv"
date: 2007-03-02
forum: Multimedia &amp; Video
---

### Post by Sengkim on 2007-03-02
Hi all,

I've installed my ubuntu edgy, mythtv and all works fine (thanks to the manuals). However, because of a bug with my synology cubestation (reported on their support site) I can't smbmount a share drive via the /etc/fstab file as it's supposed to be done.
So I'm looking for an alternative.

I followed the page [https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend) to install mythtv. There, I had to create a file /usr/local/bin/mythtv.sh that gets executed when the user logs in (mediapc in my case).

So my plan was to add the following 2 lines:

sudo smbmount //192.168.1.40/video /pvr/video/ -o username=mediapc,password=mediapc
sudo smbmount //192.168.1.40/photo /pvr/photo/ -o username=mediapc,password=mediapc


This doesn't work. Just because I wanted to be sure (and I'm a newbee), I edited my sudoers file so that the user that logs in automatically (mediapc) may execute mount and smbmount without password.

Anyone has any help to offer or ideas? It might help other synology owners also :-)

Thanks in advance!!

BB
Peter

---

### Post by yabbadabbadont on 2007-03-02
Try adding those commands to /etc/rc.local

It is the very last thing executed during the boot process, so your network should be up and functional at that point.

---

### Post by Sengkim on 2007-03-03
Hi,

Yep it works!! Thanks for the help!

BB
Peter

---

