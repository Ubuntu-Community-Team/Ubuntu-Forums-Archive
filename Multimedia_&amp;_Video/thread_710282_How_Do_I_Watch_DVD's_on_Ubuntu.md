---
title: "How Do I Watch DVD's on Ubuntu?"
date: 2008-02-28
forum: Multimedia &amp; Video
---

### Post by CarlosinFL on 2008-02-28
I have 7.10 installed on my laptop and it uses Totem (Movie Player) however I can't watch any of my DVD's. I get an error that says it can't read from resource. It does not try and download anything - simply just fails. I can watch .WMV and MPEG movies on it however which really does not help me...

Does anyone know what exactly I need to do to get this working?

sudo apt-get -y install ??SOME PACKAGE???

---

### Post by taurus on 2008-02-28
Maybe this is what you want, [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu).

---

### Post by ycason on 2008-02-28
I've found that you need both the libdvdcss2 library and VLC player.  VLC is the only one out of Totem, Mplayer, VLC that can play DVDs correctly.  Hopefully this helps.

:popcorn:

---

### Post by CarlosinFL on 2008-02-28
Thanks for that link. I added that repo they suggested and the GPG key and all went well.

I also installed the W32 codecs and libdvdcss2 packages however now with all that installed, I get the following error for some reason...

What else is missing to simply watch and  play this DVD. I used both free & non-free packages...and this is a i386 install, not AMD64.

---

### Post by taurus on 2008-02-28
Try another player like vlc, mplayer, or even xine.

---

### Post by CarlosinFL on 2008-02-28
I would prefer to just use Totem. I'm fairly sure this is possible using Movie Player...

---

### Post by wolfen69 on 2008-02-28
vlc gets my vote. very powerful media player.

---

### Post by mapes12 on 2008-02-28
I've tried a few media players on my IBM Thinkpad T23 and in my opinion Xine is the best. Looks like you have installed the correct codec packages so that shouldn't be the problem. On my laptop when I put the DVD in the drive Ubuntu detects and it mounts it (DVD icon appears on desktop). I then launch Xine. In the Xine control panel there is an icon "DVD". I click it and hey presto, the DVD plays.

---

### Post by yabbies on 2008-02-28
make sure you have libdvdnav4 installed
it is the navigation tool for totem that allows extra content in the menus

system>admin>synaptic package manager

search for libdvdnav4

install

or

terminal

```
sudo apt-get install libdvdnav4
```

plus you need libdvdread3
to read the dvd contents

please check to make sure you have both of these packages installed

---

### Post by Bruce M. on 2008-02-28
> **Carlwill said:**
> I would prefer to just use Totem. I'm fairly sure this is possible using Movie Player...

Totem is easy, check out QuickStart (see my Sig).
You'll be watching DVD's within the hour.

---

### Post by CarlosinFL on 2008-02-29
Thanks all. I did not want this to become a "You're better off using ____"or "so and so is better for DVD's"thread. Simply I followed the 1st suggestion link and never rebooted and now it works so I cam good with Totem.

Thanks again!

---

