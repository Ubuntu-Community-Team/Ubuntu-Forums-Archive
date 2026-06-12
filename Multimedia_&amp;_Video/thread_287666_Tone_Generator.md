---
title: "Tone Generator"
date: 2006-10-29
forum: Multimedia &amp; Video
---

### Post by joegumbo on 2006-10-29
Can any here recommend an easy to use tone generator I can install?  Something that will allow me to output specific frequencies through the speakers by entering the cps (Hz).

Thank you,
-Joe G.

---

### Post by Astro96 on 2006-11-04
Try
```
speaker-test -tsine -f <Hz>
```

---

### Post by Astro96 on 2006-11-04
You can also use Audacity, which is a great audio program in general

```
sudo apt-get install audacity
```

then
```
audacity
```

Chose Generate > Tone

---

### Post by joegumbo on 2006-11-13
Hi,

I apologize for taking so long to getr back to you.  I thoyght I was subscribed to this thread, but aparently I wasn'y.  So, I was not notified when you repsonded.

The speaker test worked just fine.  Thanks.

I cannot use Audacity.  For some reason I'm having a problem with updating ubunto.  I keep getting code 111 Connection refused..

I'll try audacity after I get this worked out.

Thanks,
-Joe

---

