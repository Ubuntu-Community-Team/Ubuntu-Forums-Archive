---
title: "Black Video Picture showing"
date: 2011-11-30
forum: Multimedia Software
---

### Post by medusa569 on 2011-11-30
:(   Using maverick, I try to play video clips with either Mplayer, vlan, Gnome Media player etc.  Despite which one used , I try to play a clip from a file ( mov, wmv) on dvd disk...I get a black screen.  I can only see a quick flash of the normal picture underneath when I resize the picture screen but then it quickly flashes back to black.  Sound is normal.  The clip format doesn't seem to make a difference. It's black across the board. Any help would be greatly appreciated.

---

### Post by BC59 on 2011-11-30
Maybe you didn't install the Ubuntu restricted extras. Go to Ubuntu software center and install them from there.

---

### Post by medusa569 on 2011-11-30
> **BC59 said:**
> Maybe you didn't install the Ubuntu restricted extras. Go to Ubuntu software center and install them from there.


I did have them installed...and yet reinstalled them again just now.  It would seem something does work as I can see the picture under the resizing act....I just can't avoid this black screen  that generally starts and interferes with normal video play. 


medusa

---

### Post by BC59 on 2011-11-30
To play DVDs you have to install some libraries:

```
sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3


```

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

About the other videos, check here:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by medusa569 on 2011-12-01
Well I finally got gnome mplayer to play ! yeahooo!.  The same trouble exists with VLC but at least i have one program that works.  Thank very much !






> **BC59 said:**
> To play DVDs you have to install some libraries:

```
sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3


``````
sudo /usr/share/doc/libdvdread3/install-css.sh
```About the other videos, check here:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

