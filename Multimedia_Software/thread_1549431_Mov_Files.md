---
title: "Mov Files"
date: 2010-08-09
forum: Multimedia Software
---

### Post by hewjr1000 on 2010-08-09
I have installed every codec I can find, but I still cannot play move files.

See attached screenshot

---

### Post by threezee on 2010-08-09
install VLC its by far the best.
If not. Have you installed ubuntu restricted extras?

---

### Post by Dex73 on 2010-08-09
Threezee is right. VLC works where others fail. Plus it's much more stable and less glitchy than totum. That and I think it can be installed with synaptic. I have VLC set as my default player!

---

### Post by hewjr1000 on 2010-08-10
Yep I have VLC but same baloney & cheese, codec update required.

Will check on restricted files option thanks

---

### Post by jcolyn on 2010-08-10
The best I have found is Gnome Mplayer.

First if you have totem installed uninstall it in synaptics package manager. Then install Gecko. This will install the gecko plugins into firefox in place of totem and will install Gnome Mplayer. Next type the below into your terminal 
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list 
http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && 
sudo apt-get --quiet update && sudo apt-get --yes --quiet 
--allow-unauthenticated install medibuntu-keyring && sudo 
apt-get --quiet update
```

After it is finished installing the repository type ```
sudo apt-get update
```.

Next type ```
sudo apt-get install w32codecs
```

Reboot.....

Once done type ```
sudo apt-get install libdvdcss2
```


Reboot

This should have you up and running..

---

