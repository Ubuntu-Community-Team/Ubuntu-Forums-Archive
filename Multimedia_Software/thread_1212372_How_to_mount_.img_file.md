---
title: "How to mount .img file"
date: 2009-07-13
forum: Multimedia Software
---

### Post by AndrooUK on 2009-07-13
Hey, after searching online I can't seem to find anything on .img files.

I can mount .iso fine because I use a GUI, haha, but I don't know how to mount .img files... is there a GUI for that or some simple command?  (Only simple commands because really, I don't like to use the terminal if I can help it!)  :KS

Thanks!

---

### Post by amingv on 2009-07-13
If I'm not mistaken, Acetoneiso can mount (or convert) .img files:

[http://www.acetoneteam.org/](http://www.acetoneteam.org/)

It will need some dependencies which won't get resolved automatically (at least not last time i checked), andwhich I don't quite remember. If you do dpkg -i the deb file it will tell you the dependencies (which you can then install from the repos).

You'll probably neven need any image mounting software afther this.

---

### Post by ddrichardson on 2009-07-13
You can mount it if it was TAO:```
mkdir ~/img
mount -t udf filename.img ~/img -o loop
```

---

### Post by AndrooUK on 2009-07-13
> **amingv said:**
> If I'm not mistaken, Acetoneiso can mount (or convert) .img files:

[http://www.acetoneteam.org/](http://www.acetoneteam.org/)

It will need some dependencies which won't get resolved automatically (at least not last time i checked), andwhich I don't quite remember. If you do dpkg -i the deb file it will tell you the dependencies (which you can then install from the repos).

You'll probably neven need any image mounting software afther this.

Hey thanks!  This works great!  :p

The dependencies installed automatically, so was no hassle!  I had fun playing the game I wanted to mount... hehe!

Thanks for all the suggestions.

---

### Post by addisonadam on 2009-12-06
hi Use Power Iso to mount and Unmount Image file...

 __________________
[_Construction Games_](http://constructiongames.net)

---

### Post by PendragonUK on 2011-10-21
Acetoneiso is now in the repo, so Ubuntu 11.10 can install right from Ubuntu Software Centre.

Search Acetoneiso

---

### Post by rocksockdoc on 2012-01-10
Searching for how to mount an IMG file, I found a solution which I like better:
- [**How to mount a video *.img file in Ubuntu so that you can use it**]("http://ubuntuforums.org/showthread.php?t=1907182")

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210605&stc=1&d=1326249078[/IMG]

---

