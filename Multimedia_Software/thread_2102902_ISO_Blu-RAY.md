---
title: "ISO Blu-RAY"
date: 2013-01-08
forum: Multimedia Software
---

### Post by bman on 2013-01-08
I have a slight issue.

I have a few ripped blu-rays into ISO format from when I was on Windows.

I want to now convert them to a easier played format, MKV.

So I installed Handbrake for that just to find out that it does not support ISO files.

So I right click on the file to extract, but it does not extract the contents. It extracts items, but not the files that should be extracting.

How do I accomplish this?

---

### Post by JohnAStebbins on 2013-01-08
> **bman said:**
> I have a slight issue.

I have a few ripped blu-rays into ISO format from when I was on Windows.

I want to now convert them to a easier played format, MKV.

So I installed Handbrake for that just to find out that it does not support ISO files.

So I right click on the file to extract, but it does not extract the contents. It extracts items, but not the files that should be extracting.

How do I accomplish this?
Open a terminal window.  From the command line:
```

mkdir ISO
sudo mount -o loop,dmode=0555,mode=0444,ro <your.iso> ISO

```

Then open the ISO directory with HandBrake.  When you are finished, "sudo umount ISO".

---

### Post by bman on 2013-01-08
When it's mounted, it says it's an empty directory.

I know this isn't true, it's the normal layout of a blu-ray.

Any ideas why I can't access it?

---

### Post by bfmetcalf on 2013-01-08
Have you tried makeMKV.  It usually works pretty well for me, never tried doing exactly what you are doing though.

---

### Post by bman on 2013-01-08
Isn't makeMKV for Windows only?

---

### Post by LuciferRex on 2013-01-08
> **bman said:**
> Isn't makeMKV for Windows only?

I can't help with your ISO problem, but this I can answer....it is for Mac and Windows only

---

### Post by bfmetcalf on 2013-01-08
makeMKV works wonderful on my ArchLinux box.....

[http://www.makemkv.com/download/](http://www.makemkv.com/download/)

> MakeMKV for Linux is available on the forum page.

I would be surprised if it wasn't in the repositories even

---

### Post by mc4man on 2013-01-08
> **LuciferRex said:**
> I can't help with your ISO problem, but this I can answer....it is for Mac and Windows only

Possibly not the issue here but in any event makemkv is available for linux
[http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224](http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224)

---

### Post by bman on 2013-01-08
Not the issue, which I still want an answer.

But I love makeMKV and always used it on Windows. I am glad it's available for Linux, though not as easy as adding a PPA or Software Center lol

---

### Post by bman on 2013-01-08
Though why is it telling me it's a trial?

The windows software was free right?

---

### Post by bfmetcalf on 2013-01-08
I believe you need this....

[http://www.makemkv.com/forum2/viewtopic.php?f=5&t=1053](http://www.makemkv.com/forum2/viewtopic.php?f=5&t=1053)

---

### Post by bman on 2013-01-08
I am going to assume that is new on all versions.

I swear it was free. Kinda sucks, not going to use it enough to get my moneys worth.

---

### Post by bfmetcalf on 2013-01-08
It is free, didn't you read the link.  As long as you use that beta key it is free....

---

