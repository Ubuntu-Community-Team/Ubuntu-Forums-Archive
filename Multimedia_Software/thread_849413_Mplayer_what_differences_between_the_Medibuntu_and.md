---
title: "Mplayer: what differences between the Medibuntu and the Multiverse version?"
date: 2008-07-04
forum: Multimedia Software
---

### Post by Pjotr123 on 2008-07-04
Does anybody know what differences there are between the version of Mplayer in Medibuntu and the one in Multiverse?

Thus far, I'm sticking with the Multiverse version, because that's obviously the safest option. But what do I miss (if anything)?

---

### Post by mc4man on 2008-07-04
I'm not to sure there is any difference. Both have some things disabled. From the rules file in medibuntu source
> CONFIGURE_INPUT :=  --disable-libdvdcss-internal .....clipped
CONFIGURE_AUDIO_CODECS := --disable-tremor-internal ..... clipped There may be some other things that aren't enabled  (vs. being outright disabled)

I build my own install (right now using the medibuntu source) there are some definite advantages

---

### Post by Pjotr123 on 2008-07-04
Thanks. I'll stick with Multiverse. After all, the only things I really *need* from Medibuntu are libdvdcss2 and w32codecs.

---

