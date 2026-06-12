---
title: "Rhytmbox no longer runs!"
date: 2007-12-16
forum: Multimedia &amp; Video
---

### Post by adamprawitz on 2007-12-16
I am new to Linux.

When I try to run Rhythmbox, I get the little pointer loading graphic, and then nothing else happens.

Please help.

---

### Post by atomkarinca on 2007-12-16
In a terminal (applications > accessories > terminal) could you type

```
rhythmbox
```

and paste the output here?

---

### Post by adamprawitz on 2007-12-16
Thanks for the response.  Here is my result:

Segmentation fault (core dumped)

---

### Post by atomkarinca on 2007-12-17
Which version of Ubuntu are you using? Feisty Fawn (7.04) or Gutsy Gibbon (7.10)? If you're using Feisty AFAIK this must be bug. If you're running Gutsy, I don't know the solution but you can try removing and re-installing rhythmbox:

```
sudo apt-get purge rhythmbox
sudo apt-get install rhythmbox
```

---

