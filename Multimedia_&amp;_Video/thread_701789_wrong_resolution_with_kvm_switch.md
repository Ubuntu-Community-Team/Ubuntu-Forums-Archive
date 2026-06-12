---
title: "wrong resolution with kvm switch"
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by Absinthe Minded on 2008-02-19
Hi all,

I recently bought a KVM switch and since connecting up my monitor (usually runs at 1440X900), it now runs at 640X480.

I've read some similar posts but none answer my question. I'm new to Ubuntu, so you're gonna have to put up with some dumb questions. Don't say I didn't warn you ;)

All help gratefully received!

Cheers,
Nick.

OK, just to update - I've done some more reading and tried:

```
sudo dkpg-reconfigure xserver-org
```

after booting Ubuntu in recovery mode. I thought this might force the xorg thingy to look for the monitor again, which it did. I took the advanced option and entered the referesh rates manually but still it did no good. This started me thinking that maybe it was the cheap KVM switch - but windoze is fine through the same switch.

Oh, and one more thing. I notice that the restricted display driver is now disabled - if I re-enable and restart, the monitor displays an out of range message.

---

