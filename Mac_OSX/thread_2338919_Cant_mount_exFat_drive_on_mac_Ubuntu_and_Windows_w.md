---
title: "Cant mount exFat drive on mac Ubuntu and Windows works fine"
date: 2016-10-03
forum: Mac OSX
---

### Post by 5hutd0wn on 2016-10-03
I have a ssd with 3 partitions one linux-swap, one ext 4, and one exFat.  None of these can be mounted on a mac.  I know mac isnt compatable with ext 4 and linux swap but the exFat should mount.   Could cluster size be the problem i have over 80GiB on it so id rather not have to re copy it and reformat.





*hopes admins don't notice that this thread isn't directly ubuntu related*:P ;)

---

### Post by DuckHook on 2016-10-03
> **5hutd0wn said:**
> …*hopes admins don't notice that this thread isn't directly ubuntu related*:P ;)
*Thread moved to **Mac OSX** as the more appropriate forum.*

It is not a matter of your annoying us or our annoying you. It's simply a matter of practicality: why are you not posting this in an Apple forum? The Apple-heads can clearly offer better help for Apple OSes just as Linux-heads will offer better support for Linux OSes.

---

### Post by Bucky Ball on 2016-10-03
I know nothing (much) about Mac, but in Ubuntu we install exfat-utils and exfat-fuse to make exfat work. Can you do that on Mac? I know it has a terminal but no idea if:

```
sudo apt-get install exfat-fuse
```

... would work in it. Whatever you use to install stuff in Mac, have a look for the two bits of software I've mentioned above.

Just a thought. :)

---

### Post by 5hutd0wn on 2016-10-04
yea thats something i was wondering because i thought the exfat utility might have messed up the drive

---

