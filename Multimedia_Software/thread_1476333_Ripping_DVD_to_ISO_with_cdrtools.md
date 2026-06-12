---
title: "Ripping DVD to ISO with cdrtools?"
date: 2010-05-07
forum: Multimedia Software
---

### Post by darrelljon on 2010-05-07
How do I rip a DVD to ISO with cdrtools?

---

### Post by jbrown96 on 2010-05-07
If you just want an ISO, then use dd ```
dd if=/dev/dvd of=/DESITNATION_FILE
```

---

### Post by darrelljon on 2010-05-07
So is cdrtools only for burning?

---

### Post by darrelljon on 2010-05-08
Also will dd work for CSS DVDs?

---

### Post by mc4man on 2010-05-08
> Also will dd work for CSS DVDs?
Yes and no and also to what end?

dd will give you an encrytped (css) .iso that will playback on the pc that created it (or any install that contains the proper folder and keys in ~/.dvdcss for that title.

If the disk produces read errors (whether locally from physical damage to disk or intentional from structure protection)  then dd will fail unless you use a conv=noerror option.
Depending on where and the cause/extent of read errors you'll find dd to be a rather poor choice and may take a long time.

Better options are available for rip to .iso depending on what you want the .iso for.

---

### Post by jbrown96 on 2010-05-08
No, DD will not work for encrypted DVDs. You will get an read error fairly quickly. You will need to install libdvdread4. Run ```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

You can try the DD command again, but I have only ever ripped DVDs using Brasero.

---

### Post by mc4man on 2010-05-08
> No, DD will not work for encrypted DVDs.

It actually will though I've never seen the point of using it (dd). The exceptions were noted above, but the css encryption alone doesn't produce a read error - it's simply encrypted, not un-readable

---

