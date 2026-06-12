---
title: "Drivers and decoders installed but DVDs STILL won't work"
date: 2011-02-12
forum: Multimedia Software
---

### Post by 10wuebc on 2011-02-12
so iv installed all of the nessesary drivers and decoders to run DVDs on my Ubuntu machine but whenever i pop in a movie that was not copied it doesn't play. This perplexes me because whenever i put a burned DVD into the drive it finds it right away. Any Suggestions on how to play legit copies of DVDs?

---

### Post by ajgreeny on 2011-02-12
> **10wuebc said:**
> so iv installed all of the nessesary drivers and decoders to run DVDs on my Ubuntu machine but whenever i pop in a movie that was not copied it doesn't play. This perplexes me because whenever i put a burned DVD into the drive it finds it right away. Any Suggestions on how to play legit copies of DVDs?
Drivers and decoders, maybe, but what about libdvdcss2?  have you installed that, either from medibuntu or by running the shell script /usr/share/doc/libdvdread4/install-css.sh contained in the package libdvdread4.

See [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by 10wuebc on 2011-02-12
> **ajgreeny said:**
> Drivers and decoders, maybe, but what about libdvdcss2?  have you installed that, either from medibuntu or by running the shell script /usr/share/doc/libdvdread4/install-css.sh contained in the package libdvdread4.

See [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

i already installed all of those and still no results

---

### Post by mc4man on 2011-02-12
You may want to post some add. info for those taking a look at this.
Put a commercial dvd in the drive, wait for the drive to settle and run this, post what's in the *-cdrom: section(s)
```
sudo lshw -C disk
```
Also, when you insert a comm. dvd and go to Places > computer, is the drive still shown or does it disappear?

---

### Post by 10wuebc on 2011-02-12
> **mc4man said:**
> You may want to post some add. info for those taking a look at this.
Put a commercial dvd in the drive, wait for the drive to settle and run this, post what's in the *-cdrom: section(s)
```
sudo lshw -C disk
```
Also, when you insert a comm. dvd and go to Places > computer, is the drive still shown or does it disappear?

heres what it says

*-cdrom                 
       description: DVD-RAM writer
       product: DVDRRW GSA-H30L
       vendor: HL-DT-ST
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: S856
       serial: [HL-DT-STDVDRRW GSA-H30L S85607/02/08&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

---

