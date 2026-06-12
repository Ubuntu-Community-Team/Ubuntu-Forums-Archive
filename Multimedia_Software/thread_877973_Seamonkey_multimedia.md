---
title: "Seamonkey multimedia"
date: 2008-08-02
forum: Multimedia Software
---

### Post by Torsion on 2008-08-02
Hello, I've enjoyed the tutorial on how to get all the plugins working with Firefox and everything worked perfectly, but I was wondering if someone could help with getting these same plugins working with Seamonkey.

I've managed to get flash working but not quicktime trailers or any other streaming video.  Tried to copy plugins over to Seamonkey plugins folder but that didn't seem to work.  I have Seamonkey installed in /usr/lib.  Thanks for the help.

---

### Post by sisco311 on 2008-08-02
download the mozilla-mplayer plugin:
```
sudo aptitude download mozilla-mplayer
```

extract the files:
```
 dpkg -x mozilla-mplayer*.deb /tmp
```

and copy the plugins in the seamonkey directory:
```
sudo cp /tmp/usr/lib/mozilla/plugins/* /usr/lib/seamonkey/plugins/
```

restart seamonkey.

---

### Post by Torsion on 2008-08-02
I think something might have happened after 12 updates installed with update manager today, because now Quicktime doesn't work in Firefox nor in Seamonkey even after installing mplayer.  Would anyone know what might have happened?

---

