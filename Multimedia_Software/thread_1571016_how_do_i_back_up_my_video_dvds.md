---
title: "how do i back up my video dvds ?"
date: 2010-09-09
forum: Multimedia Software
---

### Post by twidget on 2010-09-09
Hi,
I'm trying to find a good way to rip my dvd collection to .iso files so that i can back them up on my media server. my eventual goal is to be able to play these on my htpc over the network. note before anyone gets pissy: there is no piracy involved, I own all of the dvds that I will be ripping.anyway I've gotten as far as installing all the necessary codecs (i think) off of the medibuntu repos  but brasero fails at 97% or so and while k3b does complete the rip, if i try using gnome mplayer, vlc or movieplayer to play the iso all i get is either the FBI warning or at most the dvd menu before the program crashes. anyone have any idea what I'm doing wrong or how i can do it better?

---

### Post by cchhrriiss121212 on 2010-09-09
Whenever I have wanted an .iso copy I just use copy and paste, which has always worked OK. You might be suffering from a bad DVD drive, does it work OK for other things like playback?

---

### Post by indytim on 2010-09-09
If you have the storage space, this may be an alternative (my main backup app):

[http://www.fsarchiver.org/Main_Page]("http://www.fsarchiver.org/Main_Page")

I boot to this and run the above on a weekly basis for all of my partition level backups (17):

[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

Hope this helps.

IndyTim / DataMan

---

### Post by wkulecz on 2010-09-09
I use DVDrip to produce the VOB files and then cat do: xxx-00?.vob > moviename.mpg

I then copy the mpeg files to a usb hard drive for playback on our Viewsonic (linux inside!) VMP-70 media player set top box.  This is great for my wife, as she is always waking me up to help her navigate the stupid DVD menus to watch a movie.   Now she just navigates to the movie and it just plays.

Works great, upconverts the 720x480 DVD files to 1080i component and they look great on our 65" set.  Our DVD player appears to have died, not sure if I will even bother with buying a new one.

---

