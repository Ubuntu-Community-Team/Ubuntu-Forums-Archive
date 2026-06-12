---
title: "VLC Media Player"
date: 2006-10-24
forum: Multimedia &amp; Video
---

### Post by sohaibma on 2006-10-24
I am trying to download vlc media player ([http://www.videolan.org](http://www.videolan.org)) for my ubuntu 6.06 LTS. the problem is that my internet connection is extremely slow (even slower than 56k), therefore i am unable to download vlc through (synaptic package installer and terminal both). is there any way to directly download the installer file for ubuntu from windows xp on my office pc which has faster connection.

OR
if you know another way to view Divx movies in linux please tell me.

first solution is preferable but second one will also do.

---

### Post by Kateikyoushi on 2006-10-24
You can list the necessary packages for installing vlc with this command.

```
sudo aptitude -s install vlc
```

Then you can download these packages anywhere and install at home.

---

### Post by Peter76 on 2006-10-24
In synaptic check all the dependencies you need and then in your office go to packages.ubuntu.com and download them there... Then install the through Gdebi or through the command line:

sudo dpkg -i package-you-want-to-install

---

### Post by sohaibma on 2006-10-24
the problem with synaptic is that when i search for vlc it does not show up. when i made the required changes in the repositories, and press the reload button many packages donot get downloaded. maybe these two problems are related.

can you help me out here?

and please, if possible, also send me the links to the packages by checking them in your PC.

---

