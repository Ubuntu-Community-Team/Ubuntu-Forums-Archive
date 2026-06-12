---
title: "Darktable - Poor quality export files"
date: 2013-03-25
forum: Multimedia Software
---

### Post by josesanders on 2013-03-25
I'm trying to export RAW files of pictures I took with a canon DSLR.  The picture looks fine in the Darktable display, but when I export it, it gets very grainy.  Is there any way to improve the quality?  It seems to me that I should be able to get it looking at least as good as I can with a screenshot.  I uploaded an example, not sure if you'll be able to see it (I'm new to flickr, not sure how it works)
[http://www.flickr.com/photos/94362672@N05/8590115239/](http://www.flickr.com/photos/94362672@N05/8590115239/)

---

### Post by tgalati4 on 2013-03-25
Try exporting to jpg and compare.

---

### Post by josesanders on 2013-03-25
That's what I did.  I tried jpg (at 100% quality) as well as png, tiff, and a few others.  The results were the same for all.

---

### Post by josesanders on 2013-03-25
I installed a utility to read the RAW files in GIMP, and I'm having the same problem there.  So it doesn't seem to be a problem just with Darktable.  I am increasing the exposure a bit on the RAW file, so maybe that's the problem?  But it seems to me that I should be able to get it to look as good as it does on the screen before I export it.

---

### Post by tgalati4 on 2013-03-25
Try downsampling.  What is the native resolution of this camera?  There was no EXIF data in the flicker photo.

---

### Post by josesanders on 2013-03-25
I think the issue is just that the jpeg just has a lot of noise, but the display in darktable and GIMP filter it out.  If I view the jpeg files using the Ubuntu image viewer, they look noisy, but if I view the same jpeg in GIMP, it looks like it does before I export.

---

### Post by flbl on 2014-02-16
Hello,
I've exactly the same problem, with the same noise. But strangely, I remember a time when it worked ! I think it was before 13.10, maybe 13.04 or 12.10. When I exported in JPG in darkatable, I had good quality pictures. I don't know if it's because of an other version, or because I changed some settings (but I don't know what)&#8230; but I can assure you that it worked ! :)

If anyone know where can we find some details&#8230; another forum dedicated to darktable, or whatever&#8230; thanks in advance.

---

### Post by davy3 on 2014-05-13
Hi,

I'm facing the same issue running Ubuntu 13.04. I first thought it was a Darktable issue, but then noticed that it's a more general Ubuntu problem. Viewing the RAWs gives the same problem. Processing the RAWs in e.g. Lightroom gives perfect quality. But processing it with Darktable in Ubuntu gives high grain.

I have processed RAWs in Darktable before, running Ubuntu 12.04. No issues then.

No idea so far what could be causing this, but it is sure it's a general Ubuntu issue... Anyone running 14.04 and tested this already? Just open up a RAW (here in Shotwell) should be sufficient to see the grain.

Regards



> **flbl said:**
> Hello,
I've exactly the same problem, with the same noise. But strangely, I remember a time when it worked ! I think it was before 13.10, maybe 13.04 or 12.10. When I exported in JPG in darkatable, I had good quality pictures. I don't know if it's because of an other version, or because I changed some settings (but I don't know what)… but I can assure you that it worked ! :)

If anyone know where can we find some details… another forum dedicated to darktable, or whatever… thanks in advance.

---

### Post by davy3 on 2014-06-30
Just to inform I tested 14.04 myself and no problems in that release.

Regards


> **davy3 said:**
> Hi,

I'm facing the same issue running Ubuntu 13.04. I first thought it was a Darktable issue, but then noticed that it's a more general Ubuntu problem. Viewing the RAWs gives the same problem. Processing the RAWs in e.g. Lightroom gives perfect quality. But processing it with Darktable in Ubuntu gives high grain.

I have processed RAWs in Darktable before, running Ubuntu 12.04. No issues then.

No idea so far what could be causing this, but it is sure it's a general Ubuntu issue... Anyone running 14.04 and tested this already? Just open up a RAW (here in Shotwell) should be sufficient to see the grain.

Regards

---

