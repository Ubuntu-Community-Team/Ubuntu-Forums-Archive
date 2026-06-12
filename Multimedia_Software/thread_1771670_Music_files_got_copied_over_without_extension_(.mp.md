---
title: "Music files got copied over without extension (.mp3)"
date: 2011-05-30
forum: Multimedia Software
---

### Post by user1397 on 2011-05-30
I got around 6,000 songs that I copied from my ipod to my external hard drive through rhythmbox, but for some reason it didn't copy over any extensions (all of my music files are mp3's) so I was wondering what would be a really simple way to add the extension to all the files in the music folder.  My folders are setup like /Music/Artist/Album/song.mp3 (well right now there is no .mp3 but ya get the point :)

---

### Post by lordadi on 2011-05-30
You'd have to use scripting, are you comfortable with this idea?

You basically need to modify [this]("http://www.thingy-ma-jig.co.uk/blog/19-04-2008/how-batch-rename-files") to suit your needs. I think that should do it.

---

### Post by flick on 2011-05-30
Looks like a bug has been filed, but not much work done on it yet :

[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/700257](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/700257)

---

### Post by user1397 on 2011-06-03
> **lordadi said:**
> You'd have to use scripting, are you comfortable with this idea?

You basically need to modify [this]("http://www.thingy-ma-jig.co.uk/blog/19-04-2008/how-batch-rename-files") to suit your needs. I think that should do it.
I don't know much scripting, I wouldn't really know how to modify that...:(

---

### Post by Toz on 2011-06-03
**[COLOR="Red"]Before I provide a solution I must make a warning.[/COLOR]**
Make a backup of your mp3 files before proceeding.
Make absolutely sure that you run this script at the base directory of where your mp3 files are and not anywhere else. Be doubly sure!

Here is a command you can type in a terminal window that will append **.mp3** to **_all_** files in a directory structure. Again, make sure you execute the command at the base directory of your mp3 files. For example, if all of your mp3 files are located in your ~/Downloads/mp3 folder, then:

Open a terminal window (did you backup the files?)
```
cd ~/Downloads/mp3
```
```
find . -type f | xargs -t -i mv {} {}.mp3
```

---

