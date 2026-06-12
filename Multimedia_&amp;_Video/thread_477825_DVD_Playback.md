---
title: "DVD Playback"
date: 2007-06-18
forum: Multimedia &amp; Video
---

### Post by ldarkwarriorl on 2007-06-18
Hi.  I'm very new to Linux.  I just installed and updated my Feisty Fawn version of Ubuntu and I cannot play DVDs.  When i insert a disc a message pops up saying, "CANNOT MOUNT VOLUME Invalid mount option when attempting to mount the volume 'VideoDVD'."  

I'm able to access the files in dvd data discs but i can't watch movies.  Can anyone help me?

---

### Post by Gremlinzzz on 2007-06-18
you can try codecs and a new player [https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)
[http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/)

---

### Post by raymer on 2007-06-18
ldarkwarrior,
> **ldarkwarriorl said:**
> Hi. I'm very new to Linux. I just installed and updated my Feisty Fawn version of Ubuntu and I cannot play DVDs. 

 
Check out the page here [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
 
Basically you need to install three things to enable DVD playback in Feisty -
1. & 2 ```
sudo apt-get install libdvdread3 libxine1-ffmpeg
```
3. ```
sudo /usr/share/doc/libdvdread3/install-css.sh
```
 
Hope this helps,
Ray

---

### Post by ldarkwarriorl on 2007-06-18
Hey, the SMPlayer works great!

Thanks a lot!

---

