---
title: "Imagemagick convert -&gt; preserve cration date"
date: 2008-10-03
forum: Multimedia Software
---

### Post by mogliii on 2008-10-03
Hi,

not sure if this is the right forum for this question:

I installed nautilus-image-converter, this allows to rotate pictures using the nautilus context menu.
Works fine, however after rotating, the "Date Modified" is set to today. But obviously I want to know when it was created, not when rotated.

I could not find any option in the imagemagick documentation of the convert program to preserve this date.

Or is there a better way to implement loss-less picture rotaion in Nautilus?

Any help appreciated.

---

### Post by daimondI on 2008-10-04
> **mogliii said:**
> Hi,

not sure if this is the right forum for this question:

I installed nautilus-image-converter, this allows to rotate pictures using the nautilus context menu.
Works fine, however after rotating, the "Date Modified" is set to today. But obviously I want to know when it was created, not when rotated.

I could not find any option in the imagemagick documentation of the convert program to preserve this date.

Or is there a better way to implement loss-less picture rotaion in Nautilus?

Any help appreciated.
how or where can i get it to down load?

---

### Post by daimondI on 2008-10-04
> **daimondI said:**
> how or where can i get it to down load?

i need a video codec to download

---

### Post by IgnorantGuru on 2008-10-04
Not sure about a convert option, but you can use the jhead program (in repos) to do lots of things.  In your case it can set the file date to the exif date.  So after you rotate your pics run

```
jhead -ft *.jpg
```

Also, jhead can autorotate pics as well, providing your camera stores the orientation.

---

