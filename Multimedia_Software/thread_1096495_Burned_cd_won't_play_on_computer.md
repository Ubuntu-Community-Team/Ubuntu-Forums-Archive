---
title: "Burned cd won't play on computer"
date: 2009-03-15
forum: Multimedia Software
---

### Post by chadjensen on 2009-03-15
I have a problem that is not really a ubuntu issue but I am still unsure about how to go about fixing it.
  I have 8.04 and my friend gave me a cd that he made(He was the actual artist) It was burned and labeled by an outside business. I tried to back the cd up in my computer and Ubuntu recognizes the cd as a blank disk. I have listened to it for several days on my car cd player so I know it is a good cd. I looked at the cd and it appears that the first small part of the cd doesn't look like it has been burned. How would I get around this to back up my cd? I googled it and got a bunch of questions about why my computer won't recognize a blank cd. 
Any help would be great
Thanks
Chad

---

### Post by lykwydchykyn on 2009-03-15
You can try this, it may not work:
```

dd if=/dev/cdrom of=~/myfriendscd.iso && eject

```
That should pull an .iso image of the CD.  If that works, then you can burn it in brasero/k3b/whatever, or from the CLI like so:
```

cdrecord myfriendscd.iso && eject

```

Not sure why it thinks the CD is blank, but sometimes CDRWs are dodgy like that.

---

### Post by chadjensen on 2009-03-15
got this 

 dd if=/dev/cdrom of=~/myfriendscd.iso && eject
dd: reading `/dev/cdrom': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.0696337 s, 0.0 kB/s


and this for my other cd rom 

 dd if=/dev/cdrom1 of=~/myfriendscd.iso && eject
dd: opening `/dev/cdrom1': No medium found

---

### Post by chadjensen on 2009-03-15
if I go through nautilus and right click on the blank cd and choose properties and click on the volume tab it shows the size as being 2.0 kb So it is seeing the first little part as blank

---

