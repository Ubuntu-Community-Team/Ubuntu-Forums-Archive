---
title: "how to check if a monitor/tv is on or off with ubuntu core?"
date: 2019-07-16
forum: Multimedia Software
---

### Post by matteoraggi on 2019-07-16
On Raspbian I am using tvservice to check if a tv or monitor is on or off, how can I check it with ubuntu core?

---

### Post by again? on 2019-07-16
Not sure what you need but you can use xrandr to check what connection you are using.
```
xrandr -q | awk '/ connected/{print $1}'
```

---

