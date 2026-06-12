---
title: "totem doesn't play avi movies"
date: 2008-03-14
forum: Multimedia &amp; Video
---

### Post by pguerrier on 2008-03-14
I am NEW to Ubuntu and currently installed 7.10 on my laptop. I am trying to watch my avi movies using Totem player (default). It doesn't work ...says something about "requires a codec".

I tried to install via the following:
go to --> Applications --> Add/Remove Applications -->..search for "ubuntu- restricted extras" and installed it ..(i think) ..the checkbox is STILL NOT CHECKED...after I reloaded it...

also...if it is installed, where(what directory) does it put it in?

I also ran a command called
sudo get-apt install ubuntu-restricted-extras

but it says it couldn't find package "ubuntu_restricted-extras"

is there an EASIER application with codecs to play AVI, MPEG movies .???

Someone please HELP... I'm NEWBIE to Ubuntu 

thanks

Patrick

---

### Post by taurus on 2008-03-14
Check your /etc/apt/sources.list to make sure you have all the repos enable.

```
cat /etc/apt/sources.list
```

---

### Post by Keith Hedger on 2008-03-14
Try installing avi_demux

---

