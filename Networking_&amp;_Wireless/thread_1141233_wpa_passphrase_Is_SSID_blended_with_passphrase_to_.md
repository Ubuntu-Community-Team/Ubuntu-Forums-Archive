---
title: "wpa_passphrase: Is SSID blended with passphrase to make key?"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by spaceboy909 on 2009-04-28
I don't want to have to change the ascii passphrase on my friend's computer (for various reasons), so whatever tool I use to generate a key with, it needs to produce the hex equivalent  of the original ascii passphrase.

But the description of wpa_passphrase makes it sound like it is going to blend the SSID and original passphrase to create a completely different key, which doesn't correlate to the original passhrase!  :-k

Make sense?  The generated hex key should technically be able to convert back to the original ascii passhrase.

If it indeed does blend the two, then can you recommend a different key generator/converter please?

---

### Post by jtniehof on 2009-04-28
What is actually used in communication is the hex key. If you use an ASCII passphrase, that passphrase is blended with the SSID to make a key. If you know the passphrase and the SSID, [this site]("http://www.xs4all.nl/~rjoris/wpapsk.html") will give you the hex key. (It's intentionally hard to go the other way.)

---

