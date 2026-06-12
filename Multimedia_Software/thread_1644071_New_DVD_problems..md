---
title: "New DVD problems."
date: 2010-12-12
forum: Multimedia Software
---

### Post by PeachSqueezer on 2010-12-12
First off, i use Ubuntu 10.04 as my main system and if its necessary for what ever reason, (games, lazyness, etc.) i have Windoze 7 as a dual-boot.
Now, on to the problem. I prefer to use VLC media player, because it can play almost anything and its simple and cross platform. I installed libdvdcss2, and medibuntu repo as soon as i had the computer running, and have had no problems until recently playing any DVD's other than damaged ones. I have found that the movie *Iron Man 2 *and *Avatar the Last Air Bender* will open to the DVD menu just like any other DVD, but as soon as i select a scene or play it shows a black screen and unloads the disk and idles. I've also tried movie player, which promptly crashes as soon as you click play, and even tried VLC on windoze, none of them work. So far the only thing i can play it with is a DVD player and windows media player (which isn't really an option to watch any and every new movie on.)
Any ideas? 
and p.s. i no longer have Iron man 2, i use netflix, and its not fun to send a movie back unwatched.

---

### Post by mc4man on 2010-12-12
Some titles will cause issues with players that use the current libdvdread4 (nav) due to structure protection
I don't think Avatar is one, the Last Air Bender certainly is, not sure about Iron Man 2.
For the Last Air Bender, open the title in vlc - go to main menu - chapters and select chapter 1. It should then play fine.

(note that xine players that use the xinelibs version of dvdnav will have no issue, that's one reason I've keep totem-xine alive here in maverick and natty

Edit: another way for 'air' would be to go from terminal
```
vlc dvd://@11
```

---

### Post by PeachSqueezer on 2010-12-12
OK, thanks for the quick and reliable response. Now, playing from chapter one, instead of just playing worked for the last air bender, but it did not work for the backup i have for that movie (i own it) in vlc.

And just a curious question, you said that it was a structure protection problem, (something that libdvdread4 handles?) is that something that future releases of the "libdvd" and such will correct? Or should i use my good friend Google to figure that one out :p. FIREFOX! TO THE INTERWEBS! O:)

Again thanks for the help.

---

