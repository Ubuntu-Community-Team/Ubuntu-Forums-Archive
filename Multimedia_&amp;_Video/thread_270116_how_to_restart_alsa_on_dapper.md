---
title: "how to restart alsa on dapper?"
date: 2006-10-02
forum: Multimedia &amp; Video
---

### Post by ryu kun on 2006-10-02
```
sudo /etc/init.d/alsa restart
``` doesn't work...

---

### Post by henriquemaia on 2006-10-03
```
sudo /etc/init.d/alsa-utils restart
Password:
 * Shutting down ALSA...                                                 [ ok ]
 * Setting up ALSA...                                                    [ ok ]

```

Like this.

---

### Post by ryu kun on 2006-10-03
thank you.

---

### Post by jackchen on 2007-12-29
i have a 'command not found' message

for = sudo /etc/init.d/alsa restart

sudo /etc/init.d/alsa-utils restart

works but doesn't solve my problem

---

### Post by hotdoog on 2008-01-10
I also tried to "reset" instead of "restart" alsa which seemed to work but not fix my problem of no sound. I finally ejected my DVDs from the drives. This worked. I guess somehow they were still hogging the sound? Not sure if that was the same problem you had but it works for me!

---

