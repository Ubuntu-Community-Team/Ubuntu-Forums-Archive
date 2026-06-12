---
title: "append problem by using avidemux"
date: 2009-12-23
forum: Multimedia Software
---

### Post by dinw3 on 2009-12-23
Video dimensions don't match.

You cannot mix different video dimensions yet. Using the partial video filter later will not work around this problem. The workaround is:

1) "Resize" / "Add Border" / "Crop" each stream to the same resolution
2) Concatenate them together

i am trying to append two videos into one but doesnot work

---

### Post by dinw3 on 2009-12-26
i am still newbie help please :(

---

### Post by chewearn on 2009-12-26
As stated by the error message. you need to make both videos to be same dimension.

The error also suggested some options:
1. Resize (stretch) the smaller video to match the bigger video's dimension
2. Resize (shrink) the bigger video to match the smaller video's dimension
3. Add blank borders to the smaller video to match to the bigger video's dimension
4. Crop the large video to the smaller one (some picture area will be lost in the cropping)

You operate one of the option above to one of the video.  After that, you can redo the append again.

---

