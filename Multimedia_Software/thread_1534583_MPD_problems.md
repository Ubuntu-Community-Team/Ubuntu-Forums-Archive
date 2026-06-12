---
title: "MPD problems"
date: 2010-07-19
forum: Multimedia Software
---

### Post by itismesteve on 2010-07-19
I am trying to install mpd, but I get this error when running

/etc/init.d/mpd start 
mpd --create-db

listen: bind to 127.0.0.1:6600 failed: Address already in use (continuing anyway, because at least one address is bound)

and then it appears it's hanging or something

mpc update --wait hangs indefinitely.

any help much love.

---

### Post by MadCatmkII on 2010-07-22
I have that exact problem. I tried setting the adress to my computer name (as per my hosts file, this would result in 127.0.1.1) But no go. Any ideas would be highly appreciated.

---

### Post by EReckase on 2010-08-22
Try setting

```

bind_to_address		"any"

```
in your mpd.conf file.

---

### Post by Gen2ly on 2011-10-08
Exit mpd and try again.

```
mpd --kill
```

You'll have to wait a bit (two minutes??) for mpd to shutdown.

---

