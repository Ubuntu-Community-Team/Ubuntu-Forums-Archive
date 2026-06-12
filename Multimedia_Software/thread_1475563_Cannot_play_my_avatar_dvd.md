---
title: "Cannot play my avatar dvd"
date: 2010-05-07
forum: Multimedia Software
---

### Post by bagpussnz on 2010-05-07
Hi,
So I enjoyed avatar, so bought the dvd. 
I can watch it on my home theatre dvd player, but I can't watch it on my Ubuntu 10.04 computers.

I've install the usual css stuff ...

sudo /usr/share/doc/libdvdread4/install-css.sh

(and even rebooted!)

But it displays in all the players like it's encrypted. I've read the talk of it being drm protected, etc.

Is there any way round it? Or do you just torrent it (so much for being legit).

Regards.

---

### Post by bagpussnz on 2010-05-07
Hi,
Thanks for the reply. I don't get an error. I have tried playing the dvd in vlc, totem and mplayer - The dvd menu shows fine, but when you select play, it shows encrypted garbage.

I installed the libdvdcss stuff and it made no difference. 
I've also install ununtu-restricted-extras.

The dvd itself plays fine on dvd players - so it's not that.

Cheers,
Ian

---

### Post by madphatboy2 on 2010-05-07
I had this exact same issue last week. I installed the medibuntu package and it allowed me to play it with no probs.

---

### Post by bagpussnz on 2010-05-07
Hi,
Could I ask which medibuntu package?

Cheers,
Ian

---

### Post by bagpussnz on 2010-05-07
Hi,
Further to this - the avatar dvd works in ubuntu 9.10.
I have installed all medibuntu packages on my 10.04.
I can play other dvd's on my 10.04 - just not avatar.

Any ideas would be welcome.

Regards,
Ian.

---

### Post by bagpussnz on 2010-05-07
Hi,
Embarrassed. The fix was to remove my ~/.dvdcss folder - to force livdvdcss to reread the keys.

After that, It worked fine.

Thanks for your help,
Ian.

---

