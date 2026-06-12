---
title: "Emprex 3009ARF"
date: 2011-02-06
forum: Mythbuntu
---

### Post by simonnev on 2011-02-06
Due to the location of my htpc no line of sight, I purchased a rf remote, only certain keys work, anyone got a Emprex 3009ARF and managed to get all the keys working?


Thanks Simon

---

### Post by nickrout on 2011-02-06
> **simonnev said:**
> Due to the location of my htpc no line of sight, I purchased a rf remote, only certain keys work, anyone got a Emprex 3009ARF and managed to get all the keys working?


Thanks Simon

google found this:

[http://www.hardill.me.uk/wordpress/?p=34](http://www.hardill.me.uk/wordpress/?p=34)

But if you follow the link to the kernel patch required, the opinion is expressed that udev should manage this.

If you want an RF remote that DOES work, the ps3 bluetooth  remote and a simple cheap bluetooth dongle will work, I can hunt out the url with instructions if you are interested.

---

### Post by simonnev on 2011-02-07
thanks 

i take this is the one [http://www.mythtv.org/wiki/Sony_PS3_BD_Remote](http://www.mythtv.org/wiki/Sony_PS3_BD_Remote) 

i will order one today seems there is more info on this unit and i have bt dongle somewhere

thanks again simon

---

### Post by hardillb on 2011-02-07
> **nickrout said:**
> google found this:

[http://www.hardill.me.uk/wordpress/?p=34](http://www.hardill.me.uk/wordpress/?p=34)

But if you follow the link to the kernel patch required, the opinion is expressed that udev should manage this.


Having tried the udev route before writing the blog post you linked to, I can say that at the HID layer still didn''t read all the keys, but the patch is easy enough to apply, it's just a shame that at least on Fedora when I use it, the HID stuff is not a module so it needs a whole kernel rebuild.

I suppose next time I get a kernel drop I should go through the udev route again to see if things have improved.

The Emprex remote once working is very very good for the price.

---

