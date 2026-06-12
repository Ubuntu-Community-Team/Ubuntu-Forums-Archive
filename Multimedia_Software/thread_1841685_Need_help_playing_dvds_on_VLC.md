---
title: "Need help playing dvds on VLC"
date: 2011-09-09
forum: Multimedia Software
---

### Post by anomynous_mouse on 2011-09-09
Need some help. Really new to Ubuntu....

I've just installed VLC on Ubuntu Natty. It didn't play my dvd so I installed ubuntu-restricted-extras and also libdvdread4. I was also getting this message  "vlc is unable to open the mrl 'dvd:///dev/dvd'. check the log for details." So I went to Open Disk, and selected my dvd, but now I don't even get an error message and still the dvd doesn't play. 

Does anyone know what else I can do to make the dvd play?

---

### Post by mc4man on 2011-09-10
Run this in a terminal & see if it helps out any
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by handy on 2011-09-10
There is a great sticky at the beginning of this sub-forum, it is well worth reading.

Have a look at these, afterwhich you should have a good understanding of how Ubuntu handles certain kinds of files that have questionable legality (primarily in the U.S.):

[https://help.ubuntu.com/community/RestrictedFormats/#Playing%20Restricted%20Formats](https://help.ubuntu.com/community/RestrictedFormats/#Playing%20Restricted%20Formats)

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by anomynous_mouse on 2011-09-12
mc4man, thanks for this, I got it running now.

handy, I've read the links. They were a great help. I'm so glad you linked to them, I gained quite a bit of knowledge. [:

---

