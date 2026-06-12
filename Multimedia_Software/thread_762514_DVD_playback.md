---
title: "DVD playback"
date: 2008-04-22
forum: Multimedia Software
---

### Post by stokerw on 2008-04-22
Hi, I'm new to Ubuntu, still struggling a bit, and just can't get DVD to playback. I've read lots of things about this but still can't do it.
I've installed libdvdread3, but Totem does not seem to recognize that it's there.
What else do I need to do?
Thanks. Stoker.

---

### Post by cor2y on 2008-04-22
you also need libdvdcss2 for decrypting encrypted dvds aka commercial dvd movies.
Your best bet is to visit the medibuntu home page ([www.medibuntu.org](www.medibuntu.org)) either add their repos to your source list (they show you how) or individually download specific packages like libdvdcss2 (again they show you how) and also to replace totem-gstreamer with totem-xine since totem-gstreamer does not yet have dvd menu navigation all it will do is play the main dvd movie good if thats all you want but bad if you want to navigate to other sections of the dvd.

---

### Post by stokerw on 2008-04-22
Thanks for that advice. I've done as you suggested.
installed totem-xine. Can see it in Application list
installed libdvdcss2. Can't see where its installed, but when I tried a second installation it offered to replace it, so guess it must be there

Still no joy. A freebie life on earth just says there is "no plugin to handle this movie".
Titanic just shows a window "Select Movies or Playlists"
Because I'm so new with Ubuntu I don't know what to try next.
Any other suggestions gratefully received. Thanks.
Stoker.

---

### Post by cor2y on 2008-04-22
Ran into this problem with gutsy gibbon for totem-gstreamer because gstreamer got broken in gutsy.
Remove these packages via synaptic.
totem-gstreamer, totem
Reinstall these packages then try again.
Keep in mind this is only if the medibuntu repos were added to your source list if it was not some of these packages will not show up in synaptic when you search for them.
libdvdcss2, libdvdread, libdvdnav, libxine1, libxine1-ffmpeg, totem-xine, totem,  w32codecs.
Then try dvd playback again

---

### Post by stokerw on 2008-04-22
Brilliant :):)
Some of the files were not installed. Once I had checked them all out and installed them the DVD's played at once.
Many thanks - and another contribution to my steep learning curve!

One curious thing about the DVD player is that it does not have a stop button! Is that normal?

Thanks again. Stoker.

---

### Post by cor2y on 2008-04-22
only play and pause i am afraid using totem-xine if you require a stop button you will have to use either mplayer, vlc, xine-ui or gxine.

---

### Post by stokerw on 2008-04-22
Thanks again. Closing thread.
Stoker

---

### Post by enchantedsky on 2008-04-23
THANK YOU, your message got my Ubuntu to play commercial DVDs

Medibuntu's instructions actually didn't work on my Hardy Heron installation.......it played DVDs, but had no menu navigation, so I was stuck on previews for many of my DVDs

---

