---
title: "DVD player....doesn't play"
date: 2010-01-10
forum: Mythbuntu
---

### Post by Jeconti on 2010-01-10
DVD playback does not work with any of the three major players I try.

for starters, for reasons passing my understanding, my system identifies the DVD drive as /dev/sr0

The entry in Mythfrontend correctly points to /dev/sr0

The entry in DVD player settings has been attempted in three ways.

Entry: vlc dvd:///dev/sr0 %d -fs -zoom -vo xv
Result: Pressing play DVD does absolutely nothing

Entry: xine "
Result: Same, does nothing.

Entry mplayer "
Result: Program goes dark for about a minute, boots mplayer, and the picture is either just a gray box, or a digitally distored image that does not play.

---

### Post by akand074 on 2010-01-10
That's because of laws its restricted so its not allowed by default. To enable dvd playback open the terminal and paste this:

```
sudo apt-get install libdvdread4
```then 

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```should work after that in any player

If you have already done that then beats me.

---

### Post by Jeconti on 2010-01-10
Thanks, I hadn't yet installed the css. This does get mplayer to finally open the disc, but it doesn't work with any of the other programs. When the DVD boots, it loops an intro at least three times before getting to the menu, and then nothing but the mouse works.

Is there a way to just force it to use the internal player?

---

### Post by ubnewbie2 on 2010-01-10
> **Jeconti said:**
> Thanks, I hadn't yet installed the css. This does get mplayer to finally open the disc, but it doesn't work with any of the other programs. When the DVD boots, it loops an intro at least three times before getting to the menu, and then nothing but the mouse works.

Is there a way to just force it to use the internal player?

I think you just replace the vlc command with the word 'internal'.

---

