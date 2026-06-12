---
title: "w32codecs? (PLF ubuntu has shut down)"
date: 2006-10-27
forum: Multimedia &amp; Video
---

### Post by n00b0id on 2006-10-27
Where to find these codecs?

The PLF ubuntu repository has been shut down - see [http://plf.zarb.org/](http://plf.zarb.org/) for info.

---

### Post by Kateikyoushi on 2006-10-27
Try this

```
wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb
sudo dpkg -i w32codecs_20060611-0.0_i386.deb
```

Source. [LINK]("https://help.ubuntu.com/community/RestrictedFormats#head-fb5aea408a5e1bcc63400bda9300800bc65b272a")

---

### Post by mr_pouit on 2006-10-27
> **n00b0id said:**
> Where to find these codecs?

The PLF ubuntu repository has been shut down - see [http://plf.zarb.org/](http://plf.zarb.org/) for info.

It is still maintained ;) 

See: [http://doc.ubuntu-fr.org//doc/plf](http://doc.ubuntu-fr.org//doc/plf)

---

### Post by termite on 2006-10-27
packages.freecontrib.org has not been resolving for the last 36 hours.  Anyone have any ideas?

---

### Post by asipi on 2006-10-27
> **mr_pouit said:**
> It is still maintained ;) 

See: [http://doc.ubuntu-fr.org//doc/plf](http://doc.ubuntu-fr.org//doc/plf)

no it isn't :( 
it is unavailable

---

### Post by Kalinda on 2006-10-27
Yeah, I noticed it doesn't work anymore... and the only w32codecs I can find are older then the ones on the MPlayer homepage which, apparently, support WMV9.

I tried downloading them and copying them to the /usr/lib/codecs folder.. but they don't work. I guess I'm stuck with the older ones.. but does anyone know how to make it work?

---

### Post by termite on 2006-10-27
check out [http://www.debian-multimedia.org/index.html](http://www.debian-multimedia.org/index.html)

I don't have time to work on it right now, but might figure it out later.

---

