---
title: "commandline dvd backup"
date: 2007-02-09
forum: Multimedia &amp; Video
---

### Post by bionnaki on 2007-02-09
I would like to use the commandline more. So, just curious what is the best way to backup a dvd using no-gui?

I currently have dvdbackup and it works great. but what should I do with the AUDIO_TS & VIDEO_TS files that I end up with? I'd like to create an .iso. how do I use mkiso?

thanks

---

### Post by HenrikAn on 2007-02-09
You could try [vobcopy]("http://vobcopy.org/projects/c/c.shtml").

---

### Post by andrew.46 on 2007-08-06
Hi,

 Found this slightly older post:

> **bionnaki said:**
> I would like to use the commandline more. So, just curious what is the best way to backup a dvd using no-gui?

I currently have dvdbackup and it works great. but what should I do with the AUDIO_TS & VIDEO_TS files that I end up with? I'd like to create an .iso. how do I use mkiso?

thanks

 Possibly you have found a solution to your question but the best way IMHO is to use vobcopy rather than dvdbackup and then use mkisofs to generate the iso. An example would be:

```
cd Desktop
vobcopy -v -m /media/cdrom0
cd <MOVIE Folder>
mkisofs -v -dvd-video -o ../MOVIE_Name.iso 
```

 This can work with CSS dvds if the appropriate decss package is installed and this is legal where you reside.

                           Andrew

---

