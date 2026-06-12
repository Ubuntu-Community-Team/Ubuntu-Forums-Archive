---
title: "Imagemagick Vs. GIMP for JPEG"
date: 2007-10-23
forum: Multimedia Production
---

### Post by mikeym on 2007-10-23
Could someone explain to me why Imagemagick seems to produce a much lower quality JPEG at any given file size than the GIMP?

This is the command I'm using to convert using Imagemagick's mogrify command:

```
mogrify -sample 600x600 -quality 80% -sampling-factor 1x1 -antialias *.JPG
```

---

### Post by mikeym on 2007-10-23
[The GIMP 80% 63kB]("http://ubuntuforums.org/attachment.php?attachmentid=47454&d=1193158454")
[ImageMagick 80% 96kB]("http://ubuntuforums.org/attachment.php?attachmentid=47453&d=1193158454")

---

### Post by mikeym on 2007-10-23
Attached files

---

### Post by jespdj on 2007-10-24
The left image looks like it has been sharpened. Are you downsizing the image at the same time? Are you using the same resizing algorithms in GIMP and ImageMagick?

Note that there is no standard for the JPEG quality setting: what one program calls "80%" is not necessarily the same as what another program calls "80%". Some software doesn't even work with a percentage, but with a scale 1-10 or 1-12 (Photoshop), for example.

---

