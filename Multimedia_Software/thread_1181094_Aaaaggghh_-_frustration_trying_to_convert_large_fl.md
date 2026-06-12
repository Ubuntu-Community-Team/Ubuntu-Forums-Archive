---
title: "Aaaaggghh - frustration trying to convert large flac library to mp3"
date: 2009-06-07
forum: Multimedia Software
---

### Post by nothingspecial on 2009-06-07
I`ve done this before, that is why it`s so frustrating.

I have a large (approx 400 gig) Flac library. It resides on a external hard drive connected to my headless "media server" (which is just my old desktop).

I have, for a while, been using [mp3fs]("http://mp3fs.sourceforge.net/"). It mounts your flac collection as a directory full of mp3s that don`t actually exist until you "read" them. This is fine manging one iPod. You copy the tunes to your laptop, it converts them (is the phrase "on the fly"?), you put it on your ipod. No problem. I don`t have an ipod big enough to hold the lot so it was just a case of removing a couple of things evey so often and replacing them. Not a big job.

Now my whole family have ipods (4 in total - wife and kids). I find myself endlessly doing this. We have a family computer with four accounts. My plan is to convert the whole lot to mp3 to put on the family pc`s hard drive. Set up Banshee (or Rhythmbox - whatever) and show them how to do it.

No problem

```
mp3fs /media/tunes/flac,128 /media/tunes/mp3fs -o allow_other,ro
```
```

scp -rv /media/tunes/mp3fs/ me@192.168.2.5:Music
```

Wait a day or 2 - job done ......... no.

After a few gigs I get

```
cp: cannot stat Transport endpoint is not connected
```
Apparently this is a 6 month old+ bug with fuse that has yet to be resolved.

Ok I`ll use [flac2mp3]("http://bytemonkey.org/flac2mp3/"). It`s worked like a charm before but every 50 songs or so it exits without a useful error. I`ve tried messing about with it but I`m pretty useless at bash scripting.

Soundconverter is just not having it. Come back after an hour and it is still greying out and having spasms.

So, where I`m up to is connecting said drive to the family pc and using Banshee to covert them as it loads them - a useful and excellent feature. But this means I have to use my great big backup drive to stream my music and videos from the server, this means it is constantly mounted and in use.. Now, I have other copies of these (the music  being on the drive now connected to the family pc); but having lost the lot before - 400gig+ of music!!!!!!; I like to use the backup drive once a week then unmount it to lessen the risk of mass data loss. Being a victim I`m paranoid.

So help me please - if you got the end of this - please. How can I convert all the flac files in one job lot. Without spending the rest of my life doing it bit by bit or buying another externel drive simply because I can`t seem to manage this.

Thank you if you`re still reading and more thanks in advance if you can help.

---

### Post by nothingspecial on 2009-06-16
Hooorrraaay!!!! for soundkonverter. 

I don`t usually like to use kde apps, not because I`ve got anything against them but because I like pure gnome.

The best thing is we had a power cut and my stupid pc went down. $**!$@~! I thought. But I launched soundkonverter and it just picked up where it left off. Cool.

I`d still like to know why mp3fs(fuse) and flac2mp3 didn`t work though.

---

