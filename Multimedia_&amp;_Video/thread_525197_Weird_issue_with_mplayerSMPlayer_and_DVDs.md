---
title: "Weird issue with mplayer/SMPlayer and DVDs"
date: 2007-08-14
forum: Multimedia &amp; Video
---

### Post by GFree678 on 2007-08-14
First off, I've installed all the necessary libs I know of and I **can** view DVDs in Feisty already. However, I have an issue with trying them in SMPlayer (and mplayer for that matter, though it's the same engine).

I tell it to play a DVD, it starts playing the first vid on the disc (generally a short movie of the distributor's logo for example), and then... it repeats the same damn logo, and again and so on. I checked the playlist and it doesn't want to move off dvd://1 once it's played it, it just starts from the beginning. I can manually select the right vids using the playlist but that's not right, it should just advance as normal.

VLC works with DVDs properly, but I prefer using SMPlayer. Any ideas would be useful.

---

### Post by rvm4000 on 2007-08-14
Do you have the option Play->Repeat checked?

'Cos in that case of course it will repeat the same title once and again.

---

### Post by GFree678 on 2007-08-14
Well hot-damn, it worked, sorta. It never went to the menu, it merely advanced to the next vid entry in the playlist, which happened to be the main movie. Something to fix?

Also, I used qtconfig to change the default ugly theme used by QT to Clearlooks, and THAT was a big mistake. You might be interested to know that with Clearlooks, the toggle-menus like Repeat do not actually show a visible difference (i.e. the arrow isn't indented when Repeat is selected). With Clearlooks, it's exactly the same, which is why I didn't know repeat was still on. I changed it to Plastique and now it looks nice still, but the Repeat also looks indented when selected. What a stupid design flaw in Clearlooks. :)

---

### Post by rvm4000 on 2007-08-14
> **GFree678 said:**
> Well hot-damn, it worked, sorta. It never went to the menu, it merely advanced to the next vid entry in the playlist, which happened to be the main movie. Something to fix?

I'm afraid dvd menus are not supported yet (take a look at the [FAQ](http://www.phpbbplanet.com/smplayer/viewtopic.php?t=202)).

> **GFree678 said:**
> Also, I used qtconfig to change the default ugly theme used by QT to Clearlooks, and THAT was a big mistake. You might be interested to know that with Clearlooks, the toggle-menus like Repeat do not actually show a visible difference (i.e. the arrow isn't indented when Repeat is selected). With Clearlooks, it's exactly the same, which is why I didn't know repeat was still on. I changed it to Plastique and now it looks nice still, but the Repeat also looks indented when selected. What a stupid design flaw in Clearlooks. :)

I realized of that problem too, and I also stopped to use Cleanlooks because of that.

There could be an alternative: [QtCurve](http://www.kde-look.org/content/show.php/QtCurve+(KDE4%2C+KDE3%2C+%26+Gtk2+Theme)?content=40492)

[[IMG]http://img297.imageshack.us/img297/7597/qtcurve3qk6.th.jpg[/IMG]](http://img297.imageshack.us/my.php?image=qtcurve3qk6.jpg) [[IMG]http://img297.imageshack.us/img297/83/qtcurve2wn2.th.jpg[/IMG]](http://img297.imageshack.us/my.php?image=qtcurve2wn2.jpg)

---

