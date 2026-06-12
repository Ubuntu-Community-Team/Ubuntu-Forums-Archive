---
title: "mplayer .avi"
date: 2006-12-05
forum: Multimedia &amp; Video
---

### Post by stardusk on 2006-12-05
I tried to play a .avi file with mplayer and a error shows up: error opening/initializing the selected video_out (-vo) device.

I have not downloaded/installed any codecs for mplayer yet. Is this a problem? Can you tell me where/how to get codecs? Thanks in advance.

---

### Post by drphilngood on 2006-12-05
See here:
[MULTIMEDIA AND PROPRIETARY/RESTRICTED FORMATS]("http://doc.gwos.org/index.php/MultimediaCustomizationGuide#SECOND_STAGE_:_MULTIMEDIA_AND_PROPRIETARY.2FRESTRICTED_FORMATS")

and here:
[RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats#head-c268ba69c6b38af1dc31ea09701c7d296cf971c3").

Hope this helps.

---

### Post by zgornel on 2006-12-07
Try from the command prompt: ```
mplayer -vo x11 -zoom filename.avi
``` Try replacing **x11** with **xv** or *opengl* if it does not work. Also the **zoom** option is only for the **x11** driver.

---

### Post by OmniCloud on 2006-12-20
OK I've downloaded the codecs and most of vids I played works in my VLC...but the other day I downloaded a MPEG-4 Gran Turismo file and it wouldn't play. I thought VLC supported this?

---

