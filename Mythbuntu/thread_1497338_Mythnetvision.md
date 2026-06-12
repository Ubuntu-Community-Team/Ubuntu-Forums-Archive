---
title: "Mythnetvision"
date: 2010-05-30
forum: Mythbuntu
---

### Post by dfacto on 2010-05-30
For anyone having trouble with Mythnetvision causing a mythfrontend segfault on page load (or same behavior when attempting to use flash in Mythbrowser) try:

```

sudo mv /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so.ignore
```

As always, your mileage may vary!

---

