---
title: "Ubuntu 14.04 dvd movie not playing"
date: 2014-12-22
forum: Multimedia Software
---

### Post by jamarsh123 on 2014-12-22
DVD player seems to work with vlc on some dvd's, but I just popped in a Sony Pictures movie on DVD and nothing works. I've tried Totem and VLC.

---

### Post by Dennis N on 2014-12-22
Have you installed the necessary file for encrypted DVDs?

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

see section "Installing libdvdcss" (libdvdread4 is already installed so the first command isn't needed -  just the second one.)

---

### Post by Bucky Ball on 2014-12-23
Also, do you have ubuntu-restricted-extras installed and the third-party software repo enabled in your sources?

---

### Post by jamarsh123 on 2014-12-23
Thanks for the responses. I've checked via Synaptic Packet manager and everything appears to be installed. I thought it might be a faulty dvd, but I booted in to Win 7, and everything works.

---

### Post by sammiev on 2014-12-23
Try this from within Terminal.

```
sudo apt-get install libdvdread4
```

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by SeijiSensei on 2014-12-23
This thread might help: [http://ubuntuforums.org/showthread.php?t=1885267](http://ubuntuforums.org/showthread.php?t=1885267)

---

### Post by jamarsh123 on 2014-12-23
Well, I thought I had done this, but I did it again just to be sure.  It seems that I had failed to run the second command that installs it.  I've done it now, and everything seems to be working fine.  My oversight. Thanks for your help.

---

### Post by jamarsh123 on 2014-12-23
Thanks everyone for the helpful and timely responses.
Regards
jamarsh123

---

### Post by Bucky Ball on 2014-12-24
All good and great you got it working. Please mark thread as solved to help others. Thanks. (See the link in my signature for how).

Good luck. ;)

---

