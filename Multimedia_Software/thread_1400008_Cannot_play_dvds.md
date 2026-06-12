---
title: "Cannot play dvds"
date: 2010-02-06
forum: Multimedia Software
---

### Post by walterw on 2010-02-06
Hi all,

I am having problems playing dvds on my laptop which is a bluray player.  I cannot even play regular dvds, I can read them and see there is stuff there, but cannot play them in mplayer or totem.

dmesg:
[10187.795408] end_request: I/O error, dev sr0, sector 72260
[10187.795416] __ratelimit: 90 callbacks suppressed
[10187.795423] Buffer I/O error on device sr0, logical block 18065
[10187.796929] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10187.796938] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[10187.796948] Info fld=0x4691
[10187.796952] sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
[10187.796964] end_request: I/O error, dev sr0, sector 72260
[10187.796970] Buffer I/O error on device sr0, logical block 18065


Any ideas what I'm missing, I have dvdnav, read, and most other libraries installed?

Walter

---

### Post by bumanie on 2010-02-06
Have a look [here]("https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD") - it may help

---

### Post by walterw on 2010-02-06
Thanks for your post, however, as I stated, this is with regular dvds too.  I cannot play anything in the drive.

I just stated it was a bluray player so if there were any known limitations with that piece of hardware in general.


Walter

---

### Post by mc4man on 2010-02-06
AS far as regular dvd's - do you have libdvdcss2 installed?
to ck.
```
locate libdvdcss.
```
to install (if libdvdread4 is installed

```
sudo /usr/share/doc/libdvdread4/install-css.sh

```

If you're still then getting an auth. error  - has a region been set on drive ?

---

### Post by walterw on 2010-02-06
Thanks, running that script did it.  Wish this stuff was done automatically.


Walter

---

