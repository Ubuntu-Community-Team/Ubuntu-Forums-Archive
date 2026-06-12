---
title: "good dvd ripper"
date: 2009-07-30
forum: Multimedia Software
---

### Post by Jesten on 2009-07-30
i do a lot of traveling and i like to watch movies in my off time. Its so easy to just rip them to my HD. On windows i use a program called cucusoft. is there a good ripper for linux i can use. its so easy to have them on my HD after i buy them.

---

### Post by LowSky on 2009-07-30
handbreak is a great program and easiest to use in my opinion,  acidrip, dvd:rip, and a few others are not bad but you need to know a bit more, heck you can even do it from the terminal if your skilled enough

[http://handbrake.fr/](http://handbrake.fr/)

---

### Post by realzippy on 2009-07-30
..you could use dd on the terminal,what creates ISOs of your DVDs which
you can "mount" with kaffeine or other players,if you do not want any quality loss ...e.g.:

dd if=/dev/cdrom of=~/yourmovie.iso

---

### Post by Raffles10 on 2009-07-30
[dvd::rip]("http://www.exit1.org/dvdrip/") always does a good job, easy to use.

---

### Post by Jesten on 2009-07-30
thanks guys, i love this forum

---

### Post by jerome1232 on 2009-07-30
I'm going to second handbrake.

Ensure you have libdvdcss2 intalled from  the [Medibuntu Repos]("http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.medibuntu.org%2F&ei=qdtxSoOzEIKIswPksNX7CA&usg=AFQjCNFjxGqSBuIQyxKr4i9WAz1bKXzm3Q&sig2=nvTDi2UNc9GehLwf4t563Q").

I don't like that it encodes from the dvd so I use the cli utility dvdbackup to put the dvd on my hard disc drive before using handbrake to transcode. Speeds up the encoding times.

---

### Post by binbash on 2009-07-30
> **raffles10 said:**
> [dvd::rip]("http://www.exit1.org/dvdrip/") always does a good job, easy to use.

+1

---

### Post by JCarmo on 2009-07-30
I use k9copyto rip, then I mount it like this:
sudo mkdir /media/isofile
sudo mount isofile.iso /media/isofile -t iso9660 -o loop

to unmount:
sudo unmount /media/isofile

---

### Post by vinutux on 2009-07-30
Use k9copy is good for shrinking ..(without compression)

Handbrake is the best for ripping dvd (to** xvid/divx/x264 | Avi/ogm/mp4)**

---

