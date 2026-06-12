---
title: "Totem Movie Player to see DVDs"
date: 2008-10-05
forum: Multimedia Software
---

### Post by Jayhawker on 2008-10-05
Is there any way to get seeing DVDs through the Totem Movie Player. It seems codecs downloading is not allowed.

Thanks

---

### Post by Brandel Valico on 2008-10-05
[http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+playback](http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+playback)

---

### Post by Jayhawker on 2008-10-05
> **Brandel Valico said:**
> [http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+playback](http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+playback)

Thank You very much, but , is there not an easier way through the Synaptic Package Administrator?

Thanks again

---

### Post by Brandel Valico on 2008-10-05
Well you can add the medibuntu repository in synaptic.

Reload it and then simply do a search for all the various files and add or remove them as shown. Which will take roughly half an hour to and hour longer then simply copying and pasting the commands into the terminal. But yep you can use synaptic to do it all. 

Not what I would call easier.

---

### Post by minky311 on 2008-10-05
Do a search for libdvd in synaptic and install libdvdread3 and libdvdnav4.

---

### Post by Jayhawker on 2008-10-05
> **minky311 said:**
> Do a search for libdvd in synaptic and install libdvdread3 and libdvdnav4.

Already downloaded. It seems the problem is with commercial DVDs, those with zone. DVDs with universal zone works properly. Is there a way to see commercial DVDs with zone 1 or/and 2?

Thanks

---

### Post by Jayhawker on 2008-10-05
> **Brandel Valico said:**
> Well you can add the medibuntu repository in synaptic.

Reload it and then simply do a search for all the various files and add or remove them as shown. Which will take roughly half an hour to and hour longer then simply copying and pasting the commands into the terminal. But yep you can use synaptic to do it all. 

Not what I would call easier.

Thank You but medibuntu doesn't appear in "search" box of Synaptic. How can I manage this?
I've have just found out that DVD's with Universal zone does work but not those with zone 1 or 1? Any way to solve it?

Thanks again

---

### Post by gandaran on 2008-10-05
> **Jayhawker said:**
> Thank You but medibuntu doesn't appear in "search" box of Synaptic. How can I manage this?
I've have just found out that DVD's with Universal zone does work but not those with zone 1 or 1? Any way to solve it?

Thanks again
to add medibuntu follow these instructions [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
you will need to install libdvdcss2 from the medibuntu repo to play comercial dvd's
about the dvd zone you can only set your dvd player to one zone, normally it's set for your zone. you can change the zone, I don't know how many times you can change, maybe two or three, them it blocks up.

---

### Post by minky311 on 2008-10-05
Like gandaran said there is a limited number of times that you can change the region that is set on you dvd player. Try downloading regionset from synaptic to change it or install vlc which sometimes is successful in bypassing that restriction.

---

### Post by Brandel Valico on 2008-10-05
if you are able to do so set your DVD player to region 0 which is the universal no-region which should allow you to play all regions.

I'm unsure if you will be able to do so though.

---

