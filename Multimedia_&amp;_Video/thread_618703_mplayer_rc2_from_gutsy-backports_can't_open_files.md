---
title: "mplayer rc2 from gutsy-backports can't open files"
date: 2007-11-20
forum: Multimedia &amp; Video
---

### Post by oedipuss on 2007-11-20
I just upgraded to mplayer 1.0-rc2 from backports, and it shows a 'Cannot open file' message when opening any video from nautilus. 
If I run gmplayer XXXfile from a terminal , it opens normally, which is rather strange.

Also, opening a file once I've run gmplayer from terminal, via its own open file dialog, opens it, but can't decode it properly, showing a grey video window with some random noise.

Downgrading to rc1 just works, so it's not a big problem for me, but its weird
:confused:

---

### Post by frd333do33 on 2007-11-21
How do you downgrade?

---

### Post by m0u5e on 2007-11-21
you can get around the problem for now by opening using custom openwith: gmplayer %M

I think somehow gmplayer is defaulted to open files in nautilus as url links... hopes someone fixes i soon.

---

### Post by oedipuss on 2007-11-21
> **frd333do33 said:**
> How do you downgrade?

Since there's two packages, one from the regular gutsy repo and one from gutsy-backports, you can select which version you want from synaptic, Package/Force Version.

> **m0u5e said:**
> you can get around the problem for now by opening using custom openwith: gmplayer %M


Thats it, thanks :D

---

### Post by frd333do33 on 2007-11-21
Thank you. I love Ubuntu.

---

### Post by avataar on 2007-11-22
You can fix the rc2 package by opening /usr/share/applications/mplayer.desktop (e.g. run gksudo gedit /usr/share/applications/mplayer.desktop) and changing Exec=gmplayer %U to Exec=gmplayer %F

---

### Post by satkata on 2007-11-24
Thanks for the advice. I haven't thought the fix could be so simple.:)

---

### Post by Hellaxe on 2007-11-26
> **avataar said:**
> You can fix the rc2 package by opening /usr/share/applications/mplayer.desktop (e.g. run gksudo gedit /usr/share/applications/mplayer.desktop) and changing Exec=gmplayer %U to Exec=gmplayer %F

Sorry for my ignorance. What does it means changing from %U to %F?

Thanks

---

### Post by Major_Kong on 2007-12-08
%U - Tries to open the file as an URL

%F - Opens the file as it's suppose to, as a file.


PS: Such a stupid bug... Hope the package will be fixed soon...

---

### Post by Hellaxe on 2007-12-10
> **Major_Kong said:**
> %U - Tries to open the file as an URL

%F - Opens the file as it's suppose to, as a file.


PS: Such a stupid bug... Hope the package will be fixed soon...

Thank you mate.

---

