---
title: "How do you skip around in browser embedded mplayer?"
date: 2010-04-09
forum: Multimedia Software
---

### Post by benplanet on 2010-04-09
when watching a movie in browser (ff/chrome) or using mplayer to replace flash on youtube for instance, i cannot skip around the video i'm watching...

- is there a way to be able to skip forward/backwards with mplayer?

- is there a way to replace mplayer with another program that will allow me to skip?



sorry if this thread reads a bit silly, any help would be highly appreciated! thanks.

---

### Post by benplanet on 2010-04-14
I am the only ubuntu user on earth, and perhaps space, bugged by this crippling annoyance?  :)

---

### Post by WinterRain on 2010-04-14
Have you tried the vlc plugin for firefox? First remove mplayer though.

---

### Post by 2hot6ft2 on 2010-04-14
Remove any browser media player plugin you currently have installed (totem-mozilla is installed by default, but you may have installed mozilla-mplayer or mozilla-plugin-vlc) like this:
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get remove totem-mozilla mozilla-mplayer mozilla-plugin-vlc
```
You will have to enter your password which wont be displayed just type it in and hit Enter
Then install gecko media player:
```
sudo apt-get install gecko-mediaplayer
```
> Gecko Mediaplayer is the modern replacement for
mplayerplug-in (from the same author).
Then restart firefox and try it out.
:guitar:

---

### Post by benplanet on 2010-04-15
> **2hot6ft2 said:**
> Remove any browser media player plugin you currently have installed (totem-mozilla is installed by default, but you may have installed mozilla-mplayer or mozilla-plugin-vlc) like this:
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get remove totem-mozilla mozilla-mplayer mozilla-plugin-vlc
```
You will have to enter your password which wont be displayed just type it in and hit Enter
Then install gecko media player:
```
sudo apt-get install gecko-mediaplayer
```

Then restart firefox and try it out.
:guitar:

incredible, that worked wonders! thank you for the help 2hot and winterrain!

---

