---
title: "can't get &quot;VLC&quot; working"
date: 2010-07-09
forum: Multimedia Software
---

### Post by mrwicked on 2010-07-09
hi! i received my ubuntu8.10 with my dell vostro 1015 laptop.. recently i decided to  reduce the use of windows n start with ubuntu. i have a dual boot with xp sp3. after goin through a few articles, books n video tutorials , i tried to install vlc from .deb package.
this is the link where the package was mentioned "http://www.videohelp.com/forum/archive/vlc-0-9-2-deb-for-ubuntu-t357107.html" .
the package got installed successfully but when i try to play any mp3 or video file with vlc nothing happens. if anything's wrong with the package, please let me have another one("which works")....
i can't download it using the terminal because i use a dial-up modem and the driver for the modem isn't available for linux.
i use windows for surfing the web....
any help is appreciated!!!! thanks :)

---

### Post by khelben1979 on 2010-07-09
If you feel brave, you can always download the source code from [here]("http://www.videolan.org/vlc/download-sources.html").
[VLC configure parameters]("http://wiki.videolan.org/Configure#Linux") to see what you need, if anything.

I usually just do: ```
/configure
```  ```
make
```  ```
make all
```in the VLC source code file path.

PS. VLC version 1.1 is out now!

---

### Post by ron999 on 2010-07-09
But isn't VLC Media Player in the Ubuntu repository?

If so, why bother with debs or roll-your-own versions.

---

### Post by wookieshaver on 2010-07-09
I'd be interested to know if you installed the support for mp3/xvid/etc first. You can enable support for these by typing into a terminal/konsole prompt:
 
sudo apt-get install [[COLOR=#436976]ubuntu-restricted-extras[/COLOR]]("apt://ubuntu-restricted-extras/")
 
and I'd also get this one too:
 
sudo apt-get install mozilla-plugin-vlc
 
Let me know how it goes!

---

### Post by ratcheer on 2010-07-09
All I have to install to get vlc working is libdvdcss2, but that is probably included in ubuntu-restricted-extras.

Tim

---

### Post by mrwicked on 2010-07-11
no i didn't . but i'll surely let u know as soon as i install ubuntu-restricted-extras. hey do u have any idea oof a torrent link to ubuntu-restricted-extras . thanx buddy!!

---

### Post by mrwicked on 2010-07-11
> **wookieshaver said:**
> I'd be interested to know if you installed the support for mp3/xvid/etc first. You can enable support for these by typing into a terminal/konsole prompt:
 
sudo apt-get install [[COLOR=#436976]ubuntu-restricted-extras[/COLOR]]("apt://ubuntu-restricted-extras/")
 
and I'd also get this one too:
 
sudo apt-get install mozilla-plugin-vlc
 
Let me know how it goes!


no i didn't . but i'll surely let u know as soon as i install  ubuntu-restricted-extras. hey do u have any idea oof a torrent link to  ubuntu-restricted-extras . thanx buddy!!

---

### Post by martiniuuus on 2010-07-11
Is the problem you have with VLC that it doesnt work with ALL movies (like, DVD rips) - or, do you ONLY have problems with VLC with blu-ray movies (720/1080 resolutions movies)?
 
VLS supports dvd rips very good - but, it has many problems with blu-ray rips. In such case then use another player like Mediaplayer classic and with K-lite Megapack codec.

---

