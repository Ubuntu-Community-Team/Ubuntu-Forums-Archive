---
title: "VLC media player"
date: 2007-07-19
forum: Multimedia &amp; Video
---

### Post by Krishnan on 2007-07-19
Hi. Iam facing problems installing Vlc media player through Synaptic package manager. Everytime i click on Apply i get this message " Please Insert the disk labeled ApTonCD for Ubuntu Feisty- i386(2007-05-28 15:1 CD1 in drive /cdrom/

---

### Post by ubuntu.daemon on 2007-07-19
if you have ubuntu (gnome) go to admin and find the software sources, bc you might have it set up so that you need a cd for your sources.... just a guess lol

---

### Post by el-sio on 2007-07-19
When installing a program through synaptics, buntu is trying to locate the desired package on the available sources. If you are not connected to the internet, the only available sources are the packages on the installation Cds. So I suggest that you check your internet connection first (or get the Cd if you are not able to connect with this computer).
In synaptics go in Configuration -> Repositories and check the list of available sources. 
If you don't see any (except from the Cds) you should also check that you have a file called sources.list in the /etc/apt directory of your computer...
This file specifies the list of sources ubuntu is getting its packages from and should contain lines such as
 
deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) feisty main restricted 
(of cours the `jp` thing is due to my current localization...).

If not you can find help about how to create a complete source list for your version of ubuntu on the official website...

---

### Post by Krishnan on 2007-07-19
Hey El-sio as the packages you have mentioned "deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) feisty main restricted
(of cours the `jp` thing is due to my current localization...)."

I have the source list containing of 
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

---

### Post by splintercellguy on 2007-07-19
I say press Refresh in Synaptic to update the package lists, else remove the CD repository.

---

### Post by Krishnan on 2007-07-20
Thanks a lot for your replies. It really helped me

---

