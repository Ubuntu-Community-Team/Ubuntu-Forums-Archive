---
title: "Don't have permission to edit sources.list"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by Nehvrook on 2007-05-14
Hi, I'm just trying to install the codecs to get video working in fiesty (As described int he HOWTO stickied in this forum). I had no problem doing this last time, but I've since re-installed Ubuntu and now it claims I don't have permission to save changes when I try to enter 

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free 

into sources.list

Can someone help me?

---

### Post by sharke on 2007-05-14
In a terminal 
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -
In a terminal
sudo wget [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list
This will add medibuntu sources
Regards
Sharke

---

### Post by Nehvrook on 2007-05-14
That worked, thanks ^_^

---

### Post by sharke on 2007-05-14
Your Welcome
Sharke

---

