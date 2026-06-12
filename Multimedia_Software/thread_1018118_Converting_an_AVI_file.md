---
title: "Converting an AVI file"
date: 2008-12-21
forum: Multimedia Software
---

### Post by Monotoko on 2008-12-21
Hiya guys, i am wanting to convert an AVI file into DVD format so that it will go onto a DVD andplay on my damn old DVD player.

I have searched google, and all i have found is stuff for windows which i have to pay for! No offence to the people who make it, im sure its a difficult job, but im not paying £50 to convert a file into another.

Does anyone know of any linux equivilant that may convert my AVI into something my DVD player can read??

---

### Post by FakeOutdoorsman on 2008-12-21
If you like the command-line (adapted and untested by me from [[SOLVED] avi widescreen to mpg (w/ffmpeg) = squished screen](http://ubuntuforums.org/showthread.php?t=1010648) by [ClarkePeters](http://ubuntuforums.org/member.php?u=169088)):

```
ffmpeg -i input.avi -target dvd output.mpg
dvdauthor --title -o dvd -f output.mpg
dvdauthor -o dvd -T
mkisofs -dvd-video -o dvdimage.iso ~/dvd
```

Then burn iso to dvd (right click the iso file and choose "write to disk").

---

### Post by binbash on 2008-12-22
devede

---

### Post by madman100 on 2008-12-22
Hi m8 the  program i use is DeVeDe  to create video DVDs suitables for home players, from
any number of video files, in any of the formats supported by Mplayer. very easy to use all most like nero vision express 


Thanks 
madman100
:)

---

### Post by AldenIsZen on 2008-12-25
Absolutely thanks! Other programs that I have tried took a long time, more complicated, etc. Now my girlfriend's sister can watch Emment Otter's Jugband Christmas, without any gruff.

---

### Post by obsrv on 2008-12-25
I have a question too, I want to do the same sometimes, but writing a bash script isn't solution for me, because I am GUI guy, is there a GUI for these operations? :KS

---

### Post by howefield on 2008-12-25
Devede mentioned above  has a gui, so you'll be ok with that.

---

### Post by obsrv on 2008-12-25
> **howefield said:**
> Devede mentioned above  has a gui, so you'll be ok with that.

Oh, Thank you. I just didn't noticed that is a piece of software "devede"

---

### Post by smuggly on 2008-12-25
Heres A Great Link To Good Script....Smuggly

[http://ubuntuforums.org/showthread.php?t=62625](http://ubuntuforums.org/showthread.php?t=62625)

---

### Post by bttb on 2008-12-25
[Link to mencoder's documentation](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-vcd-dvd.html#menc-feat-vcd-dvd-all)

---

