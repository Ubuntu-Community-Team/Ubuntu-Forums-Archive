---
title: "Latest libgphoto2 PPA"
date: 2017-10-16
forum: Multimedia Software
---

### Post by KNRO on 2017-10-16
So I created this PPA mostly for INDI users to be used with INDI GPhoto driver, but in case anyone needs latest libgphoto2, you can use my PPA here:

[https://launchpad.net/~mutlaqja/+archive/ubuntu/libgphoto2](https://launchpad.net/~mutlaqja/+archive/ubuntu/libgphoto2)

Be warned that this builds libgphoto2 from Github on daily basis so it might be unstable!! Use at your own discretion! To install latest libgphoto2:

sudo apt-add-repository ppa:mutlaqja/libgphoto2
sudo apt-get update
sudo apt-get -o Dpkg::Options::="--force-overwrite" install libgphoto2

---

