---
title: "gnomad2 errors"
date: 2010-01-02
forum: Multimedia Software
---

### Post by jascotty2 on 2010-01-02
in my attempt to access my philips gogear mp3 player, i decided to try gnomad2. I have heard that it may work for what i want to do, but i have not been able to  get it to work..

at first, i got:
```

~$ gnomad2
gnomad2: error while loading shared libraries: libmtp.so.6: cannot open shared object file: No such file or directory

```so, after
```

sudo cp '/usr/lib/libmtp.so.8' '/usr/lib/libmtp.so.6'

```i now get
```

~$ gnomad2
Queried Philips GoGear SA60XX
Segmentation fault

```any ideas how to get this to work?

(btw, accessing the player isn't a high priority.. windows & mtpfs work, but i wanted to try out gnomad... and i don't like going to windows :))

---

### Post by Yellow Pasque on 2010-01-03
If gnomad2 was still looking for old libmtp, you may want to comment in this bug: [https://bugs.launchpad.net/ubuntu/+source/gnomad2/+bug/312807](https://bugs.launchpad.net/ubuntu/+source/gnomad2/+bug/312807)

---

