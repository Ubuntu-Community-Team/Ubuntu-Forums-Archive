---
title: "Cannot change subtitle size in totem-xine"
date: 2007-03-31
forum: Multimedia &amp; Video
---

### Post by ihatethedekoys on 2007-03-31
I cannot change the subtitle size in totem-xine, under the preferences window. Or in /home/username/.gnome2/totem-conf. if I change it in totem-conf from "small" to "large" and launch totem, totem automatically resizes back to small in totem-conf. /home/username/.xine/config has it set to large as well. And gxine uses the large font. Is there any way to up the subtitle font size in totem-xine?

---

### Post by henriquemaia on 2007-04-04
> **ihatethedekoys said:**
> I cannot change the subtitle size in totem-xine, under the preferences window. Or in /home/username/.gnome2/totem-conf. if I change it in totem-conf from "small" to "large" and launch totem, totem automatically resizes back to small in totem-conf. /home/username/.xine/config has it set to large as well. And gxine uses the large font. Is there any way to up the subtitle font size in totem-xine?

I have the same question. How can one change this? And besides the size, the subtitles are so offset to the bottom of the screen that I get tired of always having to look to the movie and to the bottom to read the subtitles (in different moments).

---

### Post by Rusna on 2007-04-21
I've same problem, it would be nice to know how to adjust the subtitle size to normal instead of small.
I'm using Feisty ans totem-xine and the file to edit is (I think) ~/.gnome2/totem_config and there lines:

> 
# subtitle size
# { tiny  small  normal  large  very large  huge }, default: 1
#subtitles.separate.subtitle_size:small

# subtitle vertical offset
# numeric, default: 0
#subtitles.separate.vertical_offset:0

# font for subtitles
# string, default: sans
#subtitles.separate.font:sans

# encoding of the subtitles
# string, default: iso-8859-1
subtitles.separate.src_encoding:utf-8

# use unscaled OSD if possible
# bool, default: 1
#subtitles.separate.use_unscaled_osd:1

# default duration of subtitle display in seconds
# numeric, default: 4
#subtitles.separate.timeout:4

Is there some backup config file that need also be deleted or something?

---

### Post by Rusna on 2007-04-22
Solution:

Pay attention:

WRONG: ```

# subtitle size
# { tiny small normal large very large huge }, default: 1
#subtitles.separate.subtitle_size:small
```

RIGHT: ```

# subtitle size
# { tiny small normal large very large huge }, default: 1
subtitles.separate.subtitle_size:small
```

So basically the thing what we we're not seeing was commenting out =)

---

### Post by pmj on 2007-04-23
It's impossible to change fonts when using totem-xine. The function that sets the font is empty, save a comment that says "FIXME" or somesuch.

You might be able to change it for xine somehow, though, which should change it in totem-xine as well, as totem-xine doesn't touch fonts.

---

