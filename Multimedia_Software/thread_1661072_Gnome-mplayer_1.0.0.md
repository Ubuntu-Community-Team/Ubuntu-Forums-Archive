---
title: "Gnome-mplayer 1.0.0"
date: 2011-01-06
forum: Multimedia Software
---

### Post by JJJJoke on 2011-01-06
Could not compile gnome-mplayer 1.0.0 from source.
At first ./configure gives lack of gtk2.0+ and some other packets.
I installed libgtk2.0-dev. And ./configure stage done clear.
But after make get errors:
```
dbus-interface.h:31: fatal error: dbus/dbus.h: No such file or directory
compilation terminated.
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/Gnome-MPL/src'
make[1]: *** [check-recursive] Error 1
make[1]: Leaving directory `/home/Gnome-MPL/src'
make: *** [check-recursive] Error 1

```
Could not find any solutions still. Help please!

Is there any ppa for Maverick with new  Gnome-mplayer 1.0.0?
There is no VDPAU for VLC, isn't it?

---

### Post by mc4man on 2011-01-06
should build fine on mav, have svn-r1882 built here (try running sudo apt-get build-dep gnome-mplayer

Or you shouldn't have much  trouble finding a ppa, just search

Here's one that offers the latest svn (r1882
[https://launchpad.net/~ed10vi86/+archive/tst](https://launchpad.net/~ed10vi86/+archive/tst)

vlc doesn't have vdpau, supports vaapi (which is just barely ok here w/nvidia, mplayer w/ vdpau is superior

---

### Post by JeffDavidoff on 2011-01-06
The file /usr/include/dbus-1.0/dbus/dbus.h seems to be in the packet                            [libdbus-1-dev]("http://packages.ubuntu.com/maverick/libdbus-1-dev"). Do you have this packet installed? If not: ```
apt-get install libdbus-1-dev
```

---

### Post by JJJJoke on 2011-01-06
> **mc4man said:**
> should build fine on mav, have svn-r1882 built here (try running sudo apt-get build-dep gnome-mplayer

Or you shouldn't have much  trouble finding a ppa, just search

Here's one that offers the latest svn (r1882
[https://launchpad.net/~ed10vi86/+archive/tst](https://launchpad.net/~ed10vi86/+archive/tst)

vlc doesn't have vdpau, supports vaapi (which is just barely ok here w/nvidia, mplayer w/ vdpau is superior

Thank you, this help much!!!
But how have you found this ppa? I was googling about a day and found nothing?

---

### Post by mc4man on 2011-01-06
> But how have you found this ppa?
either a straight google search or you could use this page
[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

As far as recommending a ppa I prefer not to with ones that offer alot of different packages, you never know when someone may run an update and unintentionally update other things

In this case the above ppa was pretty much specific to gnome-mplayer, though you should note that there is an updated flash installer there.
If you don't want that updated then pay attention when updating or disable the ppa in 'Software Sources' till looking for an updated gnome-mplayer

---

### Post by JJJJoke on 2011-01-06
Well, thank you. I was googling a lot and find nothing (means ppa).
As to concerns this ppa, I've installed gnome-mplayer, but it was to sluggish for me. Not only when movie is played but with the interface itself without any video file... So I choose smplayer with vdpau and it works great.
As to apt-get build-dep gnome-mplayer, this works and I compile binaries at the end. But I don't want to use this one, as understand there should be much more turnarounds to be good solution. I choose smplayer.
Nevertheless, thank you very much for help!!!

---

### Post by mc4man on 2011-01-06
Atm I'm mainly using natty so haven't had a chance to compare gnome-mplayers.

Thought i'd mention this ppa, I consider highly trusted (same maintainer as ubuntu repo mplayer packages), it offers a new mplayer from the current svn every 3 days or so. (though if happy w/ what you have ...

[https://launchpad.net/~motumedia/+archive/mplayer-daily](https://launchpad.net/~motumedia/+archive/mplayer-daily)

---

