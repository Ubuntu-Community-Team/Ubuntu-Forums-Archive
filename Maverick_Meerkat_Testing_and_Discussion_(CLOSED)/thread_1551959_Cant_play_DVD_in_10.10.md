---
title: "Cant play DVD in 10.10"
date: 2010-08-13
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Kangarooo on 2010-08-13
```
Playback failure:
DVDRead could not open the disc "/dev/dvd".
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/dvd'. Check the log for details.
```

in terminal vlc opening cd:
```
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Can't stat /dev/dvd
No such file or directory
libdvdnav: vm: failed to open/read the DVD
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Can't stat /dev/dvd
No such file or directory
[0x9695e74] dvdread demux error: DVDRead cannot open source: /dev/dvd
[0x95b1d84] main input error: open of `dvd:///dev/dvd' failed: (null)

```

so i installed and after each step tryd and still didnt work:
from [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
```
sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh
```
rebooted
from [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
didnt work so changed $(lsb_release -cs) to lucid and that worked
```
sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
sudo apt-get install libdvdcss2
sudo apt-get install w32codecs
```

So ive done all & still after restarts im getting same DVD error.

---

### Post by lisati on 2010-08-13
Moved to "Maverick Meerkat Testing and Discussion".
From the banner:
> Ubuntu Maverick Meerkat is in development, use only for testing purposes!!!

---

### Post by 3rdalbum on 2010-08-13
Your DVD drive is not /dev/dvd, it's probably something like /dev/scd0.

Use Disk Utility to find out the device  file of your DVD drive and then type that into VLC's "Open Disc" window, or just drag the DVD icon from your desktop onto VLC's main window.

---

### Post by Kangarooo on 2010-08-13
Wow. Yes that worked.
But in 10.04 i even didnt installed anything and it worked by just choosing play DVD

---

### Post by ranch hand on 2010-08-13
> **Kangarooo said:**
> Wow. Yes that worked.
But in 10.04 i even didnt installed anything and it worked by just choosing play DVD
10.10 is in development.  This makes it more FUN.

You can expect it not to work at 100%.  It is not supposed to at this point.

---

### Post by punissuer on 2010-09-06
Never mind.  Installing VLC from the Ubuntu Software Center activated the needed source and installed libdvdread4.

---

### Post by kuvanito on 2010-09-06
one thing that i always do after installing ubuntu(any version) to any computer is installing the restricted extras and that will take care of almost any audio/video/playing files and more:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by punissuer on 2010-09-06
> **kuvanito said:**
> one thing that i always do after installing ubuntu(any version) to any computer is installing the restricted extras

Thanks, I did that from USC.  It didn't install libdvdread4 or activate the source needed to do so.

I'm used to having that source available.  I just didn't think to go into Synaptic and activate it.  The notice that libdvdread4 wasn't available even though an available package referenced it kinda threw me.

---

