---
title: "Issues with DVD menus on Ubuntu"
date: 2009-11-15
forum: Multimedia Software
---

### Post by beastrace91 on 2009-11-15
Hey There,

So today was really the first time I sat down and tried to play a normal DVD on my Ubuntu system and while the video itself actually plays the menus are all garbled and I have to blindly feel my way through them to play the actual video. I have the Medibuntu repos added and I installed **non-free-codecs** and **libdvdcss2** from it but alas the issue still persists for me :( Any suggestions on other things I can try?

Thanks,
~Jeff

---

### Post by wojox on 2009-11-15
Try this for 9.04 and 9.10:

```
sudo apt-get install libdvdread4
```

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by beastrace91 on 2009-11-15
No good. still having the same issue. I think it may be a codec issue though, because it happens consistently in the same parts of the menu and the same episodes on the DVDs (plays some but not others). Also happens at the same parts in both totem and VLC (and MPlayer flat out fails to load the DVD - gives me a "seek error")

Any other ideas I can try?

~Jeff

---

### Post by beastrace91 on 2009-11-15
Alright - so I was able to solve my own issue. I was poking around [here](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) and I went out on a lim checking the notes on the bottom and manually set my region (using the regionset tool) to my home region of US (which is where the DVD is from). Doing this allowed the video to play normally. It must have been off/set to the wrong location by default.

EDIT: Spoke to soon - went back to try the other video that wasn't working and it still is all pix-elated and impossible to watch :/ Open to suggestions.

~Jeff

---

### Post by alejandro.mc on 2009-12-07
I'm also having trouble, no menus in DVDs work for me..Any help? 

Thanks in advance!

---

### Post by beastrace91 on 2009-12-07
I had no luck regardless of what I did/tried. Run it through a Windows VM or just use a DVD player :-/

~Jeff

---

### Post by mc4man on 2009-12-07
Try going into your home folder ( show hidden files), find the .dvdcss folder and delete it

then try your player again

---

### Post by alejandro.mc on 2009-12-08
I did that, not working =(

Bye!

---

