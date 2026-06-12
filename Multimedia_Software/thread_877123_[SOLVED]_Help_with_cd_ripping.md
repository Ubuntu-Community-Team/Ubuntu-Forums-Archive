---
title: "[SOLVED] Help with cd ripping"
date: 2008-08-01
forum: Multimedia Software
---

### Post by wolfen69 on 2008-08-01
i have alot of cd's i would like to rip and would prefer a gui based app for this. i have tried asunder and grip. both were a no-go. k3b worked, but only gave me 128kb a sec.(i want 320 a sec) how can i change k3b's settings to give me 320kb or can someone recommend another app for this? thanks for any help.

---

### Post by mc4man on 2008-08-01
As i mentioned in your other thread Rubyripper (both a cli and gui ripper).
Otherwise if your ripper of choice will allow inserting parameters, ck. here
```
CBR (constant bitrate, the default) options:
    -b <bitrate>    set the bitrate in kbps, default 128 kbps
    --cbr           enforce use of constant bitrate

  ABR options:
    --abr <bitrate> specify average bitrate desired (instead of quality)

  VBR options:
    -v              use variable bitrate (VBR) (--vbr-old)
    --vbr-old       use old variable bitrate (VBR) routine
    --vbr-new       use new variable bitrate (VBR) routine
    -V n            quality setting for VBR.  default n=4
                    0=high quality,bigger files. 9=smaller files
    -b <bitrate>    specify minimum allowed bitrate, default  32 kbps
    -B <bitrate>    specify maximum allowed bitrate, default 320 kbps

```

---

### Post by wolfen69 on 2008-08-01
ok guys, i found ripperx which seems to work well. finally!

---

