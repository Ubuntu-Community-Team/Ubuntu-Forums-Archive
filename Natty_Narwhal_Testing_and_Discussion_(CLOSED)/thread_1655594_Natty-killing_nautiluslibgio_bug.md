---
title: "Natty-killing nautilus/libgio bug"
date: 2010-12-29
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Starks on 2010-12-29
Nautilus segfaults immediately after GDM and is preventing the desktop from loading.

```
[   27.873703] nm-applet[1355]: segfault at 4834cfd8 ip 00c5ef3d sp bfddbd20 error 4 in libgio-2.0.so.0.2705.0[b81000+106000]
[   28.719963] nautilus[1358]: segfault at 4dee0fd8 ip 002cff3d sp bfbd3d30 error 4 in libgio-2.0.so.0.2705.0[1f2000+106000]
[   29.013516] nautilus[1397]: segfault at 4dd52fd8 ip 00359f3d sp bfc54570 error 4 in libgio-2.0.so.0.2705.0[27c000+106000]
[   29.201734] nautilus[1403]: segfault at 4de28fd8 ip 005def3d sp bfd72bb0 error 4 in libgio-2.0.so.0.2705.0[501000+106000]
[   29.619391] nautilus[1406]: segfault at 4d307fd8 ip 00213f3d sp bfe597a0 error 4 in libgio-2.0.so.0.2705.0[136000+106000]
[   30.474674] nautilus[1409]: segfault at 4d2fbfd8 ip 00313f3d sp bfa8b0b0 error 4 in libgio-2.0.so.0.2705.0[236000+106000]
[   30.603033] nautilus[1412]: segfault at 4cc86fd8 ip 001edf3d sp bff52450 error 4 in libgio-2.0.so.0.2705.0[110000+106000]
[   30.725330] nautilus[1415]: segfault at 4d2b4fd8 ip 00226f3d sp bf9fec70 error 4 in libgio-2.0.so.0.2705.0[149000+106000]
[   31.182243] show_signal_msg: 3 callbacks suppressed
```

---

### Post by Starks on 2010-12-29
Never mind, I just needed to give my /home partition's dot-folders a much needed pruning.

---

