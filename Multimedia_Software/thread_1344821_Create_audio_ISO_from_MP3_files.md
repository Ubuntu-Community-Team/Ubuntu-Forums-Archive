---
title: "Create audio ISO from MP3 files"
date: 2009-12-03
forum: Multimedia Software
---

### Post by midwesterndirt on 2009-12-03
Does anyone have any idea how to create an audio ISO from MP3 files? Generating an ISO from a physical CD is possible, as is burning a physical audio CD from an ISO or from MP3s, but I have not yet found a way to do this one particular thing. I found a thread in the old forums about this, but it did not get a single response.

---

### Post by howefield on 2009-12-03
> **midwesterndirt said:**
> Does anyone have any idea how to create an audio ISO from MP3 files?

Open brasero and create data project.

Add your files/mp3 whatever and at the bottom of the screen, you'll see where it is being saved and the name of the iso, change as required.

Don't put a cd in the drive and burn.

---

### Post by arubislander on 2009-12-03
You should be able to use Brasero. Create an Audio CD project and select your mp3 files... then click on burn. When you get to the burn dialog you should be able to select an option to create an image file instead...

I'm away from my computer at the moment (how am I typing this you ask?) so I can't check my instructions...

---

### Post by midwesterndirt on 2009-12-03
> **howefield said:**
> Open brasero and create data project.

Add your files/mp3 whatever and at the bottom of the screen, you'll see where it is being saved and the name of the iso, change as required.

Don't put a cd in the drive and burn.

This creates an MP3 CD ISO, not an audio CD ISO.

> **arubislander said:**
> You should be able to use Brasero. Create an Audio CD project and select your mp3 files... then click on burn. When you get to the burn dialog you should be able to select an option to create an image file instead...

I'm away from my computer at the moment (how am I typing this you ask?) so I can't check my instructions...

You'd think that would work, but there is no option to write to image. The selector at the bottom of the window is disabled.

---

### Post by arubislander on 2009-12-03
I came across [this post]("http://ubuntuforums.org/showpost.php?p=3439214&postcount=2"). Taught me something new too.

---

### Post by midwesterndirt on 2009-12-03
> **arubislander said:**
> I came across [this post]("http://ubuntuforums.org/showpost.php?p=3439214&postcount=2"). Taught me something new too.

While I suppose that makes sense, it still baffles me that it is possible to burn to an audio disc and then create a burnable ISO from that disc yet you can't do it in one step. If what was said in the older post was true, it would not be possible to rip audio images from a physical disc, which is simply not true. Something is amiss here, but I'm not sure what it is. There has to be some way to accomplish this.

---

### Post by Melcar on 2009-12-03
Try isomaster.  Lets you create iso files.  I think AcetoneISO also can do it.

---

### Post by bulletxt on 2009-12-04
You can not do an ISO-9660 of an Audio CD. However, you can make a binary image with AcetoneISO. You can't mount it though, but you can use it as a backup and burn it in a second moment with k3b or brasero.

---

