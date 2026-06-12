---
title: "Linux DVD Player"
date: 2009-06-11
forum: Multimedia Software
---

### Post by cph05a on 2009-06-11
I'm looking for your linu DVD player of choice. I've used LinDVD in the past, but I no longer have a copy of it and I don't really want to pay for it. I've used VLC, but it only works on a few DVDs. 

What is a good (preferably free) DVD player for linux?
(If anyone suggests VLC, tell me how to get it to work right)

---

### Post by coffeecat on 2009-06-11
Are the DVDs that won't play in VLC, commercial encrypted ones? You may need to install libdvdcss2 which you can get from the [medibuntu]("http://www.medibuntu.org/") repository. Follow the 'Repository Howto' link in that link to enable the medibuntu repo, and then you'll be able to install libdvdcss2 from Synaptic.

---

### Post by cph05a on 2009-06-13
I tried installing libdvdcss2 but it did not solve the problem. Any other ideas?

---

### Post by cph05a on 2009-06-18
bump. I'd rather not buy linDVD, but I haven't had any luck with VLC or Totem. (Since last post, I've tried Ogle, but didn't like it)

---

### Post by Chronon on 2009-06-18
I find that Dragon player plays most DVDs for me, but its picture quality (deinterlacing?) seems to not be as good as VLC.  I have good success rate with VLC, though.  There's always Mplayer, I guess.

---

### Post by ~sHyLoCk~ on 2009-06-18
Mplayer works well for me without any issue.

---

### Post by surfed on 2009-06-18
xine has always been one of my faves, great menu support and picture quality.

---

### Post by jasonsjunk on 2009-06-18
VLC has worked for every commercial DVD i have ever played on it (even recent titles).  You might try uninstalling VLC and reinstalling via synaptic to make sure you have all of the required files also make sure you have the medibuntu repository enabled.  You need libdvdcss2 and libdvdread4. I believe the 2nd pkg is correct you can find it in synaptic by typing DVD in the search, its in there somewhere.

---

### Post by cph05a on 2009-06-20
> VLC has worked for every commercial DVD i have ever played on it (even recent titles). You might try uninstalling VLC and reinstalling via synaptic to make sure you have all of the required files also make sure you have the medibuntu repository enabled. You need libdvdcss2 and libdvdread4. I believe the 2nd pkg is correct you can find it in synaptic by typing DVD in the search, its in there somewhere.

This almost worked. It now opens the DVD, but the color is wrong (it looks like red is missing). Both Dragon and Mplayer failed to even open the DVD.

---

### Post by Marlonsm on 2009-06-20
Totem with Xine backend, with the ubuntu-restricted-extras package works fine for me.

---

### Post by cph05a on 2009-06-21
> Totem with Xine backend, with the ubuntu-restricted-extras package works fine for me. 

This works like a charm :) 

thanks for all the suggestions!

---

### Post by gabak on 2009-11-10
get OGLE i heard it is great !!
[http://www.dtek.chalmers.se/groups/dvd/](http://www.dtek.chalmers.se/groups/dvd/)

---

### Post by ilil on 2009-11-26
Ogle is unsupported now, all its code is in xine now. IMHO, xine or totem-xine is the best with DVD.

---

### Post by gabak on 2009-11-26
> **ilil said:**
> Ogle is unsupported now, all its code is in xine now. IMHO, xine or totem-xine is the best with DVD.

thxs
what is IMHO ??? i have have xine but there are some dvd that does nt work. or i have problem with subtitles , nothing works like powerdvd for windows

---

### Post by Shazaam on 2009-11-26
In My Honest/Humble/Holy/Hesitating/Highest Opinion

[http://www.acronymfinder.com/IMHO.html](http://www.acronymfinder.com/IMHO.html)

---

### Post by ilil on 2009-11-26
What DVD title do you speak about? I have no trouble wih all DVD I have.

---

### Post by gabak on 2009-11-26
> **cph05a said:**
> This works like a charm :) 

thanks for all the suggestions!

hey how do i do that?
i got gxine and totem-xine and none of them work great with all dvd.
plz tell me from scrach ?
let say that i just install ubuntu so now what?

i have installed vnc , dvd player and all thing related with dvd in the synaptic also some librery like libdvd or something like that.

---

