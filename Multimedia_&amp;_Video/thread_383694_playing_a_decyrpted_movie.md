---
title: "playing a decyrpted movie"
date: 2007-03-13
forum: Multimedia &amp; Video
---

### Post by ljonesj on 2007-03-13
i got the movie to start playing but i cant choose the play all or audio or setup in the dvd menu and half way through playing of the music it cuts out and sometimes it does not so what can i do to get it to work i can stream it from the server to my laptop which runs xp home and it works fine

---

### Post by ssavelan on 2007-03-14
xine or gstreamer?

---

### Post by ljonesj on 2007-03-14
totem movie player but xine and gsteamer do it too. but i do prefer totem so thats the one i am more concerned about

---

### Post by ssavelan on 2007-03-14
Yes, but regular Totem runs gstreamer, I believe; but, you can have Totem-xine instead.

From my experience, I would definitely go with Totem-xine.  Then you can use:

***
libxine-extracodecs
***

and

totem-mozilla(i think.. the totem plugin, whatever it is called)

I have not personally gotten the regular totem to do much.  Totem-xine with the extracodecs does almost everything.  The only other media players I use are RealPlayer and Flash.  I have done a good bit with a bunch of other programs (VLC, Kaffeine, etcetc) but have never had much luck with non-xine (ie gstreamer, eh?) types.

This is admittedly a rather nubish path.  Some people swear by VLC for everything; I'm not saying it is best, just, in my experience, the easiest and most painless.

---

### Post by ljonesj on 2007-03-14
well found out something my synaptic package manager keeps giving me a error about a wrong password i got ubuntu to run my mp3 collection and this started happing after i got it workinking i done this before and it has never happened when i went into synaptic so i cant update to totem-xine now

---

