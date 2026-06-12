---
title: "Unable to play Videos"
date: 2013-02-06
forum: Multimedia Software
---

### Post by FahadMKS on 2013-02-06
Hi,

I have just installed the Ubuntu 12.04 to my new Lenovo Laptop. All the updates has been installed and still I am unable to play any of the videos on the movie player. 

The issue is that it asks to install certain plugins so as to get the videos working.
So I installed the Ubuntu restricted extras from the software center and I am still unable to get my videos working.

I have attached a file so as show the issue in detail.
Please do help me with this issue.

Thanks

---

### Post by andrew.46 on 2013-02-06
Perhaps bypass the problem by installing SMPlayer and vlc, both much more capable than Totem:

```

sudo apt-get install smplayer mplayer vlc libavcodec-extra-53

```

Hope this gets your movies started up...

---

### Post by FahadMKS on 2013-02-06
Thanks for the reply.. but I got the issue resolved by myself. Changed the settings in the software sources and got the plugins installed. Now everything seems to be working fine.

Thanks again for the help.

---

