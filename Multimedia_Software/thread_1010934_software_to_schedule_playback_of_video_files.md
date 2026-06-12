---
title: "software to schedule playback of video files"
date: 2008-12-14
forum: Multimedia Software
---

### Post by orangeek on 2008-12-14
Hi all.
I'm looking for an application that lets you schedule the playback of video (/audio) files; like on monday at 8AM play the IdontLikeMondays.avi file, then at 1PM the lunch.avi file and so on.
I see a lot of commercial applications like mediashout, designed to manage video kiosks but none of them is free (as in beer :AND as in speech, since I want to build a whole-open system).

Any hint?

I was already looking on some custom webpage from them you can specify day of the week and time and let choose the file; then a script will gather this information and put them on a crontab file.

thank you
orangeek

---

### Post by iponeverything on 2008-12-14
```
sudo nano /etc/crontab
```

for the format:

```
man 5 crontab
```

---

### Post by orangeek on 2008-12-14
thank you, you're really helpful.
I'm looking for something else than a custom webpage used to insert crontab entries.

---

