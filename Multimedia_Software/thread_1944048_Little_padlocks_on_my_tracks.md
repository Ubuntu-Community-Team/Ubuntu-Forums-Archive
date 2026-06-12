---
title: "Little padlocks on my tracks"
date: 2012-03-20
forum: Multimedia Software
---

### Post by Extreedoc on 2012-03-20
The other week I bought a CD and as usual had it in mind to rip it to my computer and put it on my MP3 player. Problem: I got it on the computer alright but each track has a little padlock next to it and won't play. I'm assuming the CD is coded to stop people like me doing what I've already described; is there no way I can get it on my MP3?

---

### Post by winh8r on 2012-03-20
Were you running as root when you ripped it?

You should be able to do

```
sudo chown -R yourusername /path/to/directory
```

---

### Post by Extreedoc on 2012-03-20
> **winh8r said:**
> Were you running as root when you ripped it?

You should be able to do

```
sudo chown -R yourusername /path/to/directory
```

Thanks, I'll give it a try.

---

### Post by Lucradia on 2012-03-20
Also, sometimes putting windows owned mp3s on a flash drive will show them with padlocks. They will still play, but you can't move / edit them.

---

### Post by nothingspecial on 2012-03-21
*Thread moved to **Multimedia & Video**.*

---

