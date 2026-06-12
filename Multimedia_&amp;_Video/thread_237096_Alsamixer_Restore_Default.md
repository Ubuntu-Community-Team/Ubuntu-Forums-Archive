---
title: "Alsamixer Restore Default"
date: 2006-08-15
forum: Multimedia &amp; Video
---

### Post by Cyfr on 2006-08-15
How do I go back to the settings which were originaly in alsamixer? My sound is horrible because ive been messing, I just want it back to how it was when I first installed Dapper.

Thanks.

---

### Post by mlind on 2006-08-15
> **Cyfr said:**
> How do I go back to the settings which were originaly in alsamixer? My sound is horrible because ive been messing, I just want it back to how it was when I first installed Dapper.

Thanks.

You can use alsa-utils initscript to reset settings to sane defaults. 0 is the soundcard number, you can probably omit the value if you have only one soundcard.
```

sudo /etc/init.d/alsa-utils reset 0

```

If you want to immediately save the new settings as /var/lib/alsa/asoud.state (happens automatically on shutdown too)
```

sudo /etc/init.d/alsa-utils restart

```

---

