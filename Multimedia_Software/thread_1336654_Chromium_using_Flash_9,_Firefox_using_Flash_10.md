---
title: "Chromium using Flash 9, Firefox using Flash 10?"
date: 2009-11-24
forum: Multimedia Software
---

### Post by Grimmy on 2009-11-24
Hi,

Just installed Chromium into my fresh Karmic install using Googles .deb ( [http://dev.chromium.org/getting-involved/dev-channel](http://dev.chromium.org/getting-involved/dev-channel) ) and it seems to run fine ... however when I visit YouTube, right clicking a video reveals it to be using Flash 9.   Firefox uses Flash 10.   Flash 9 doesn't have any sound on my System  .   Anyone know how I can get the Chromium (4.0.249.11) to use Flash 10 instead of Flash 9?

Cheers,
Grimmy.

---

### Post by Grimmy on 2009-11-25
Managed to work it out...

in about:plugins both versions were listed, so I did

```

sudo updatedb
locate libflashplayer.so

```

then I used sudo rm to remove all instances of libflashplayer other than the one in /usr/lib/flashplugin-installer/libflashplayer.so

Now Chrome is using Flashplayer 10 and I have sound.

---

### Post by quantum8 on 2009-11-25
excellent, just what I needed, thanks!

---

### Post by Can+~ on 2009-12-11
Worked perfectly, although, on a fresh install, I added the folder manually, without problems:

Chromium (in the folder you have libflashplayer.so 64-bit)
```
sudo mkdir /usr/lib/flashplugin-installer
sudo cp libflashplayer.so /usr/lib/flashplugin-installer/

```

And for Firefox
```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
```

---

### Post by pansapiens on 2009-12-31
I had a similar issue after upgrading from Jaunty (9.04) to Karmic (9.10). The Firefox Flash plugin had sound but Chromium didn't.

I found that I had **adobe-flashplugin**, **flashplugin-installer** and **flashplugin-nonfree-extrasound** installed.

I removed them all:
```
sudo apt-get remove adobe-flashplugin flashplugin-installer flashplugin-nonfree-extrasound
```

Then reinstalled only adobe-flashplugin:
```
sudo apt-get install adobe-flashplugin
```

Then I restarted Chromium - YouTube videos now have sound !

*(it's possible just removing flashplugin-installer & flashplugin-nonfree-extrasound without the reinstall of adobe-flashplugin would have worked too ...)*

---

