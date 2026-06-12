---
title: "Using cdrdao to create image file ONLY"
date: 2008-12-06
forum: Multimedia Software
---

### Post by airzonk on 2008-12-06
Hi,

After googling and reading manpages to death,

I want to know how I can use cdrdao with a toc file to create a .iso or .img file -- AND NOT BURN IT TO A PHYSICAL DISK.  Or another comparable tool.  Ideas, anyone?  cdrdao will happily burn a CD for me from the toc file but that is not what I want.

Thanks,
Gabe
):P

---

### Post by infoseeker on 2008-12-07
I've used K3B (under Kubuntu) to create image files, but not under Ubuntu (or c/l for that matter) yet.

---

### Post by vanadium on 2008-12-07
Something like this?

```

cdrdao read-cd --source-device ATA:1,0,0 --paranoia-mode 3  --with-cddb audiocd.toc 

```

---

### Post by jonobo on 2009-04-17
Thread-Revival :KS

@vanadium:
I guess you got "airzonk" wrong. I think he wanted to do the same thing that i want to do right now.

I have a .wav-File and a corresponding .toc-File - normally i would burn an Audio-Master-CD from that, but right now i want to create a CD-Image right away (yeah, i could create a Master-CD first, and then rip it, but that doesn't make any sense in my case because i want to skip my potentially buggy CD-Burner and simply have a 100% clean CD-Image that i could for e.g. send to a CD-Factory (they only take fully ready single-file CD-Images) )

So, question is still open - any ideas anyone?

---

