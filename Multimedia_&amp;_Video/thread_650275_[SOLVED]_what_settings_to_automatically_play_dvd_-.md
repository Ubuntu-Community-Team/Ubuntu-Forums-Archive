---
title: "[SOLVED] what settings to automatically play dvd -- internal or external player"
date: 2007-12-26
forum: Multimedia &amp; Video
---

### Post by kishorebudha on 2007-12-26
I have two DVD drives (internal and external) and used the following settings to automatically play DVDs on insertion

wxvlc dvd:///dev/dvd

However, this only plays the DVDs inserted in internal dvd player. 

If I enter the following command, it plays from the external player

wxvlc dvd:///dev/dvd1

Is there a single command that would search for DVDs on both DVD players and play the appropriate one?

---

### Post by schaumkeks on 2007-12-26
> **kishorebudha said:**
> I have two DVD drives (internal and external) and used the following settings to automatically play DVDs on insertion

wxvlc dvd:///dev/dvd

However, this only plays the DVDs inserted in internal dvd player. 

If I enter the following command, it plays from the external player

wxvlc dvd:///dev/dvd1

Is there a single command that would search for DVDs on both DVD players and play the appropriate one?

Use special parameters:
    * %d means device node name,
    * %m means mount point name,
    * %h means HAL UDI.
(thanks to [http://people.debian.org.tw/~chihchun/2007/06/20/fix-the-vcd-auto-play-command-in-gnome/](http://people.debian.org.tw/~chihchun/2007/06/20/fix-the-vcd-auto-play-command-in-gnome/))
So your command within System->Preferences->Removable Drives and Media->Multimedia->Video DVD Discs could look like that:
```
wxvlc dvd://%d
```

---

### Post by kishorebudha on 2007-12-26
Thank you very much. That worked!!! Also, I commented out the below line from /etc/fstab 

/dev/scd0

---

### Post by Billisnice on 2007-12-26
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by kishorebudha on 2007-12-26
It was the solution by schaumkeks that I was looking for

---

