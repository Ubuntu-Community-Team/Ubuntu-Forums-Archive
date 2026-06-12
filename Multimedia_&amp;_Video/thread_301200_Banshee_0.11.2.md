---
title: "Banshee 0.11.2"
date: 2006-11-16
forum: Multimedia &amp; Video
---

### Post by spanella47 on 2006-11-16
has anyone made debs for the newest banshee 0.11.2 ?  or is there a 3rd party repo that keeps up-to-date with banshee?

since updating to edgy my banshee library has been considerably slower and often hangs when searching or when going from a playlist to my full library.  granted my library is 8000 songs or so, but even so the dapper version never had this problem and was a lot faster.

---

### Post by pay on 2006-11-16
Try compilling it for yourself. It's fun...
```
wget http://banshee-project.org/files/banshee/banshee-0.11.2.tar.gz
sudo apt-get build-dep banshee
sudo apt-get install libmono-sqlite2.0-cil libmono-cairo2.0-cil
sudo apt-get install automake1.9
sudo update-alternatives --set automake /usr/bin/automake-1.9
sudo ldconfig
sudo apt-get install libtool autoconf
sudo apt-get install checkinstall
tar zxvf banshee-0.11.2.tar.gz
cd banshee*
./configure --prefix=/usr
make
sudo checkinstall make install

```

---

### Post by spanella47 on 2006-11-17
yeah figured someone would say that, not a total newb here.  would just be easier and potentially safer with a repo and someone more experienced than myself packaging it.

---

### Post by molgar on 2006-11-27
Someone built it: [http://www.ubuntuforums.org/showthread.php?t=305075](http://www.ubuntuforums.org/showthread.php?t=305075)

---

