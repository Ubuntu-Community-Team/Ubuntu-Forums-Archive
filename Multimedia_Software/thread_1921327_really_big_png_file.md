---
title: "really big png file"
date: 2012-02-06
forum: Multimedia Software
---

### Post by 618smartguy on 2012-02-06
I was wondering if i can open a huge image without the entire image loading into ram, so that i can zoom in and load higher resolution or something of the sort. The file that I am trying to open is a png and it is over 4 GB. The default photo viewers on ubuntu just freeze, and use up about 3 gigs of ram. I was thinking maybe I should use google earth but I am not sure how to go about that.

---

### Post by erind on 2012-02-06
Can you split the big png file into smaller pieces ? If so, with ImageMagick installed, to split the file into a given number of tiles, say 4, and not needing to calculate the exact pixels, you can do:

- Sequential type:

```
 convert -crop 1x4@ Big_file.png  tile_%d.png 
```- Or in a zig-zag fashion:

```
 convert -crop 2x2@ Big_file.png  tile_%d.png
```For an exact number of pixels, say 1024x1024:

```
 convert -crop 1024x1024 Big_file.png tile_%d.png
```

---

