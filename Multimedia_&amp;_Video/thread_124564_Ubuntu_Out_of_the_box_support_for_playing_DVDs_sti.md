---
title: "Ubuntu Out of the box support for playing DVDs stinks"
date: 2006-02-01
forum: Multimedia &amp; Video
---

### Post by makoto149 on 2006-02-01
I hated to post that subject, but unfortunately, I wasn't getting many reads under the old post. It's true, though, IMHO, Ubuntu's (5.10) support for playing DVDs stinks. Maybe someone can help.

I have been running Ubuntu for a few days now. I think it's great. But today I decided to try and watch a DVD. After battling several problems (like having to install libdvdcss2) I am down to an error that a google search doesn't turn up anything useful (in English, anyway, and the google translations are NOT very good).

When I try to run Totem, I get the message "Could not read title information for DVD." This is driving me nuts. I am so glad I am dual botting with Windows XP so at least I can watch a DVD, but I would like to use Ubuntu for everything.

Has anyone run into this before? Any help is appreciated. I have tried this DVD other places and it works fine. Other DVDs that play fine elsewhere also result in this error message.

Thanks

---

### Post by Zyphrexi on 2006-02-01
You installed Automatix? It's pretty nifty. Try that.

About out-of-the box shtuff. Well i'm pretty sure all that are legal issues. You know, so ubuntu doesn't get sued or whatever for using proprietary codecs and distributing them illegally. I'm not a big fan of totem myself, vlc is purty nifty. I really don't watch all that many dvd's though. But for a lot of the pain in the butt stuff, Automatix does a good job. (win32 codecs, DMA= on, dvd stuff, etc)

---

### Post by bjweeks on 2006-02-02
Guess what if you live in the us you have to break the law to play dvds.

---

### Post by bjweeks on 2006-02-02
and Windows doesn't surport any dvd playback out of the box.

---

### Post by Lord Illidan on 2006-02-02
I use Xine to play DVDs. It is a heck of a lot better than totem, and integrates with Kaffeine, my fav multimedia player.

Just install libdvdcss (wonder why you can't find it on google, found it immediately here :

[http://download.videolan.org/pub/libdvdcss/1.2.9/]("http://download.videolan.org/pub/libdvdcss/1.2.9/")

Note : It may be illegal where you live. Just to warn you. Mods are free to take this link off.

Install the deb, and you are free to go.. Just apt-get install xine.. totem is useless..

EDIT : About Microsoft - You don't get out of the box support for DVDs and you are paying through the nose....I had to install VLC on Windows to see a DVD and play an ogg file.

---

### Post by mpvano on 2006-02-02
Better yet, once you've got xine running, you can use synaptics to install "totem-xine" which will magically replace totem's brain-dead, freeze-prone, zombie spawning totem-gstreamer back end with one that makes totem use xine to do the heavy lifting.

(You need to have the "universe" repositories active to do this, however).

This fixes all those mime types that accidentally keep forcing totem to run when it's inconvenient so they don't crash everything!

Now if only xine played quicktime movies!

Mario

---

