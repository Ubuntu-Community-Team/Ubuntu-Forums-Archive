---
title: "Network Speed"
date: 2013-06-15
forum: Networking &amp; Wireless
---

### Post by asearle on 2013-06-15
Hallo all,

In a small research project that I am involved in we have a member in Israel who regularly logs remotely into a PC in Germany.  This normally works fine.

However, over the last two weeks we have had big drops in performance, so much that she can almost not work any more.  I have tested the link more locally and it is working fine so the problem seems to be network speeds between Europe and Israel so my suspicion is that maybe network trafic in Turkey (due to the unrest there) is slowing things down.

Has anyone had similar experiences?

Are there tools or web-sites which might help me check the cause of our problem?

Many thanks for any tips that you can give me.

Yours,
Alan Searle
Cologne, Germany

---

### Post by Cheesemill on 2013-06-15
You can try running the mtr command against a remote IP address to see where the bad/overloaded link is, for example...
```
mtr 8.8.8.8
```

---

