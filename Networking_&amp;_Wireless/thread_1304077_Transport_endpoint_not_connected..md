---
title: "Transport endpoint not connected."
date: 2009-10-28
forum: Networking &amp; Wireless
---

### Post by dale456654 on 2009-10-28
Hi,
After installing xubuntu on my old 64mb laptop it was too slow, it took 20 seconds to open a terminal! I then installed Ubuntu mini with the 9mb cd. When that was done I installed everything from there, I chose IceWM with dillo. Everything was working nicely. I got sound remote desktop, but there is just one thing that I cannot get working, that is samba networks. I tried everything i could find to get it working including pyneighborhood but I get the message could not mount. I was going to install nautilus but it was 350mb! I followed a guide... [http://fromtheterminal.blogspot.com/2009/06/adding-samba-support-to-thunar.html](http://fromtheterminal.blogspot.com/2009/06/adding-samba-support-to-thunar.html) . After following this i can browse the share but i cannot do anything to it. I get the message Transport endpoint not connected. Can anyone please help me with this?

Thanks!

---

### Post by ant2ne on 2009-10-28
> **dale456654 said:**
> Hi,
After installing xubuntu on my old 64mb laptop it was too slow, it took 20 seconds to open a terminal! I then installed Ubuntu mini with the 9mb cd. When that was done I installed everything from there, I chose IceWM with dillo. Everything was working nicely. I got sound remote desktop, but there is just one thing that I cannot get working, that is samba networks. I tried everything i could find to get it working including pyneighborhood but I get the message could not mount. I was going to install nautilus but it was 350mb! I followed a guide... [http://fromtheterminal.blogspot.com/2009/06/adding-samba-support-to-thunar.html](http://fromtheterminal.blogspot.com/2009/06/adding-samba-support-to-thunar.html) . After following this i can browse the share but i cannot do anything to it. I get the message Transport endpoint not connected. Can anyone please help me with this?

Thanks!
Is this a samba server or samba client? I'm assuming client

I'd fetch all of this

sudo apt-get install -y samba
sudo apt-get install -y samba-common
sudo apt-get install -y libkrb53
sudo apt-get install -y smbclient
sudo apt-get install -y smbfs
sudo apt-get install -y ntfs-3G
sudo apt-get install -y ntfs-config

If you can connect to the share but can't do anything, then you probably don't have permissions on that share. you need samba permissions (in the smb.conf) as well as unix permissions on the file system. Does that make sense?

---

