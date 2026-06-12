---
title: "X won't start with Radeon 7000"
date: 2006-06-02
forum: Multimedia &amp; Video
---

### Post by fieldstone on 2006-06-02
I've been running Dapper beta on my laptop for several months, and yesterday I decided to replace my screwy Windows XP installation on my Desktop with the Dapper final release. The only problem is my video card doesn't seem to want to work with the ati or radeon drivers - only vesa works, and as a result my dvd playback looks horrible. I couldn't even start the installer without doing it in "safe graphics" mode - which I assume also meant vesa.

My video card is a 32 MB Radeon 7000 AGP (one of the CompUSA branded ones)... if anyone else has had a similar problem and fixed it, or can offer me any pointers, I'd really appreciate the help. (I've already tried UseFBDev in xorg.conf, with no success.)

---

### Post by Teroedni on 2006-06-02
could you paste your xorg.log it will tell why it dosent wanna load radeon.

```

sudo gedit /var/log/Xorg.0.log
```

If you have kde
```

sudo kedit /var/log/Xorg.0.log
```

---

