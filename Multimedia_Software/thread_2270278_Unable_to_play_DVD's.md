---
title: "Unable to play DVD's"
date: 2015-03-21
forum: Multimedia Software
---

### Post by myron620 on 2015-03-21
Hello everyone, I'm a semi new lubuntu user, installed 14.10 on intel desktop today. Everything works except Dvd playback. dvd player runs but no icon on desktop.

I searched the forums and found a thread from one user saying he could not play ISO. in mplayer.


Any help much appreciated.

---

### Post by MrSteve on 2015-03-21
you may need to install libdvdcss2 ...

[https://www.videolan.org/developers/libdvdcss.html](https://www.videolan.org/developers/libdvdcss.html)

---

### Post by Thuyen on 2015-03-23
> **MrSteve said:**
> you may need to install libdvdcss2 ...

[https://www.videolan.org/developers/libdvdcss.html](https://www.videolan.org/developers/libdvdcss.html)

Hi, I followed the instructions and installed the libdvdcss but I'm still not able to play my DVD.  The same DVD can be play on the vlc player (using Windows 7).  I'm still learning when it comes to linux so please excuse me for asking stupid questions.  When I installed Xubuntu I did select the extras codecs so I don't understand why I'm having such a hard time playing a DVD?  Everything else seem to be working fine.

Thanks for the help in advance.

---

### Post by Keith_Helms on 2015-03-25
If you installed xubuntu-restricted-extras, open a terminal window and run the following command:
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Then you should be able to run vlc from the Multimedia menu and select Open Disc from vlc's Media menu.

---

