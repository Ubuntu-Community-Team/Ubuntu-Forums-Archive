---
title: "Make songbird the default music player"
date: 2009-03-13
forum: Multimedia Software
---

### Post by Firidan on 2009-03-13
I want songbird to play all sound files(.mp3, .ogg ...) on my ubuntu 8.10 x64 instead of rhythmbox.

I downloaded and installed songbird.deb package from getdeb.net but songbird's not listed among the installed applications. I tried to use a custom command (/usr/bin/songbird) but when I click on a music file it just opens songbird (not the file itself!! I have still to browe for the file).

Thanks in advance!!!!!;);););)

---

### Post by mc4man on 2009-03-13
I checked songbird out a ways back and got rid of it, anyway, while you can certainly associate your various music formats, songbird won't open and play, just open.
If you add all your music to it's library i guess you won't have to search it out.
There are no commands for songbird that I saw other than songbird which as you've seen just opens it. (there's also no man or help pages


You should have gotten a menu entry and icon in Applications -> Sound & Video, if not run this. (should be the same on your 64 bit as it was in my 32 bit install

```
cp /usr/share/applications/songbird.desktop ~/.local/share/applications/songbird.desktop
```

---

### Post by sgosnell on 2009-03-13
System, Preferences, Preferred Applications.  On the Multimedia tab, pick custom and enter songbird, or whatever the name of the binary file is.

---

### Post by Firidan on 2009-03-14
Thanks

I was really hoping to make songbird my default music player. Rhythmbox does the job but songbird looks a lot better and has lots of useful add-ons.

---

