---
title: "create DVD from VOB files"
date: 2008-01-16
forum: Multimedia Production
---

### Post by famleon on 2008-01-16
I have a family dvd that is giving errors, I need to copy it, if I try to use it it does not runs in Ubuntu (funny can be opened in windows only), so I used the decripter to copy to the hard drive, after I did it I copy to the ubuntu computer (the MS computer does not have a dvd burner) but none of the programs installed has an option I google it and I was not able to find a program that does the miracle (DVD author, K9, DVD Rip, etc...)

---

### Post by Joeb454 on 2008-01-16
Try Brasero

It's in the Repo's so if you open up Add/Remove or Synaptic and search for it (make sure you search all available places)

I'd recommend it :)

---

### Post by jeffus_il on 2008-01-16
Apparently DVD Decrypter can also burn images.
[http://en.wikipedia.org/wiki/DVD_Decrypter](http://en.wikipedia.org/wiki/DVD_Decrypter)
or use [ImgBurn]("http://en.wikipedia.org/wiki/ImgBurn")

---

### Post by yabbies on 2008-01-16
vob files are mpgs

any of those programs will work
or if you have a video directory that contains all of the vob, ifo and bup files to burn you can install Tovid.

It's not in the repos but google search and it's very easy to install

After installing Tovid name the video file MyVids and put it on your desktop

open a terminal and type

```

cd Desktop
```
```

makedvd -burn MyVids
```

---

### Post by famleon on 2008-01-19
The dvd was not able to rip it in ubuntu, so i did it in ms with decripter and burn it with bracero and it is working thanks

---

