---
title: "mt-daapd &amp; ogg"
date: 2011-12-30
forum: Multimedia Software
---

### Post by frogotronic on 2011-12-30
Hello,

From the config file instructions:

```
# To be able to index .ogg files, you'll need to have configured
# with --enable-oggvorbis
```

Can someone explain this to me, I don't understand?

- CH

---

### Post by rubylaser on 2011-12-30
When you are building mt-daapd you'd need need to configure it with that option if you where building from source.  Something like this.
```
./configure --enable-oggvorbis
```

Then, 
```
make && make install
```

---

### Post by frogotronic on 2012-01-11
okay, thanks

How do I get firefly to index my music?

I've got the music folder pointed to /home/user/Music

But it hasn't indexed any of the music in that folders

Thanks

---

