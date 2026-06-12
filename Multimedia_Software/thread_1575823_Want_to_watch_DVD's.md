---
title: "Want to watch DVD's"
date: 2010-09-16
forum: Multimedia Software
---

### Post by bigseb on 2010-09-16
So my little one killed my DVD player but I want to watch DVD's. What do you recommend is the best way to do this. I thought just install VLC via Synaptic but that doesn't work, the links (or whatever you call them) aren't there any more...

[ATTACH]169635[/ATTACH]

---

### Post by solar george on 2010-09-16
You need to update your package lists as the vlc version has been updated to -1ubuntu1.2.
To play DVDs you'll also need libdvdcss from medibuntuhttps://help.ubuntu.com/community/Medibuntu#Playing Encrypted DVDs

---

### Post by jimmers on 2010-09-16
Install ubuntu-restricted-extras from synaptic, and you should be onboard.

Luck


Jim

---

### Post by solar george on 2010-09-16
> **jimmers said:**
> Install ubuntu-restricted-extras from synaptic, and you should be onboard.

Luck


Jim

ubuntu-restricted-extras does **not** include libdvdcss2 which is needed for encrypted dvd (i.e. all commercial releases) playback for that you need the medibuntu packages.
```
#apt-cache show ubuntu-restricted-extras
. . .
Please note that this does not install libdvdcss2, and will not let you play
 encrypted DVDs. For more information, see. . .

```

---

### Post by bigseb on 2010-09-17
> **solar george said:**
> You need to update your package lists as the vlc version has been updated to -1ubuntu1.2.

Worked. VLC downloaded.

> **solar george said:**
> 
To play DVDs you'll also need libdvdcss from  medibuntuhttps://help.ubuntu.com/community/Medibuntu#Playing Encrypted  DVDs

Haven't tried playing anything yet but according to synaptic libdvdcss was install along with VLC.

---

### Post by solar george on 2010-09-17
If that's the case then its very odd, libdvdcss is not in the main ubuntu archive (and is unlikely to ever be) and none of the vlc packages depend or recommend libdvdcss. VLC will however have pulled in libdvdread which does not support encrypted playback.

---

