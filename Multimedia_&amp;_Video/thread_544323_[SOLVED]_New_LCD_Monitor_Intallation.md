---
title: "[SOLVED] New LCD Monitor Intallation"
date: 2007-09-06
forum: Multimedia &amp; Video
---

### Post by jabster on 2007-09-06
Hi.

I am going to be upgrading from my 17" CRT to a 22" LCD soon and have a question.

Since I know refresh rates & sync rates in xorg.conf are important, do I need to do anything to my xorg.conf before plugging the new monitor in?

ie: Do I need to modify HorizSync & VertRefresh, and/or the Screens section before plugging it in so that nothing blows up?

thanks,
john

---

### Post by w4ett on 2007-09-07
> **jabster said:**
> Hi.

I am going to be upgrading from my 17" CRT to a 22" LCD soon and have a question.

Since I know refresh rates & sync rates in xorg.conf are important, do I need to do anything to my xorg.conf before plugging the new monitor in?

ie: Do I need to modify HorizSync & VertRefresh, and/or the Screens section before plugging it in so that nothing blows up?

thanks,
john

It is unlikely you will blow up anything :).....Set you screen resolution and refresh rates to 800x600 @60 Hz and plug in the new monitor.  (It will be ugly, but it will be safe)  You can either then do a :

```
sudo dpkg-reconfigure xserver-xorg
```

and let the utility detect your new monitor's EDID data and then reconfigure xorg.conf for you OR you can do it manually by:

```
sudo gedit /etc/X11/xorg.conf
```

and manually editing the file yourself by input of the correct resolutions and the refresh rates.

Good Luck

---

### Post by jabster on 2007-09-20
w4ett, thanks for the "sudo dpkg-reconfigure xserver-xorg" reminder there.

I did mess up and accidentally selected a couple of higher than the monitor takes...but no harm done. That why god made liveCDs. :-)

All is good now with pretty 22" monitor.

thanks,
john

---

