---
title: "Can't play protected movie DVDs"
date: 2011-04-24
forum: Multimedia Software
---

### Post by wkcchampion on 2011-04-24
I just bought the DVD of the movie tron legacy and it doesn't play on Ubuntu 10.10 with any player. I tried VLC; Totem, Kaffeine. It always says "impossible to read from disc".

I read ino ther posts that I need a package named Libdvdread4, which is installed. I tried to reinstall it with no success.

The DVD works perfectly in the home dvd player and under Windows XP. I also tried other DVDs (Transformers, Terminator and star Wars) with the same result.

Any ideas?
Thanks and happy Easter

---

### Post by andrew.46 on 2011-04-24
> **wkcchampion said:**
> I read ino ther posts that I need a package named Libdvdread4, which is installed. I tried to reinstall it with no success.

If you have successfully installed libdvdread4 you can then install libdvdcss:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

and hopefully this will be enough :).

---

### Post by wkcchampion on 2011-04-24
Yeah it worked. I wonder why this package isn't installed on Ubuntu by default...

---

### Post by andrew.46 on 2011-04-24
> **wkcchampion said:**
> Yeah it worked. I wonder why this package isn't installed on Ubuntu by default...

Great news! There is a perceived legal problem with libdvdcss in some countries hence it is not available by *default* but reasonably easy to install anyway :).

Andrew

---

### Post by bbrg548 on 2011-06-14
I'm having the same issue, but only with Tron: Legacy - my other DVDs work fine and alway have.

I have libdvdread4 and libdvdcss installed. The DVD plays through the previews, then in mplayer I get the message "Cannot read from source" and VLC just stops and drops to the control panel.

I haven't tried it in Winblows, yet.

---

