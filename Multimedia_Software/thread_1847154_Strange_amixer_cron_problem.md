---
title: "Strange amixer cron problem"
date: 2011-09-20
forum: Multimedia Software
---

### Post by ka9qlq on 2011-09-20
OK I open a terminel and type

```
amixer -c 0 sset Front,0 55%,55%
```

Does just what the manpage says but you call the same thing from a cron and it sets the speaker full blast. Same with line-in. unmute seems to work in cron. Ideas?

---

