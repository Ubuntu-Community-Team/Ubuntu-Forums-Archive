---
title: "How to tell myth to use /dev/dvd1 and not /dev/dvd?"
date: 2011-01-30
forum: Mythbuntu
---

### Post by heyho on 2011-01-30
I've just re-built my system, and reinstalled 10.04.  In testing various functions, I found that I couldn't play any DVDs.  At first I thought it was just a myth problem, but VLC was also unable to access the drive.  lshw -C disk showed that the logical name for the drive was in fact dvd1 - pointing VLC to dvd1 instead has fixed this issue, but myth must still be looking for a device which isn't there.

I tried creating a symbolic link, which seemed to work until the next re-boot.  I have also seen an example which edits a udev file, but would prefer to be able to just point myth towards dvd1 if at all possible.

Also, whilst on the subject, should I be able to watch a dvd in the backend machine from a remote frontend?  (noob question I know).

---

### Post by nickrout on 2011-01-30
yes it is in the video settings|player settings

---

### Post by heyho on 2011-01-30
> **nickrout said:**
> yes it is in the video settings|player settings

Many thanks, I think I even looked there!  I will try tomorrow when I have the box up again.

---

