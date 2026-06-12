---
title: "VLC player and subtitles"
date: 2008-02-10
forum: Multimedia &amp; Video
---

### Post by StOoZ on 2008-02-10
I cant get VLC player to open the subs automatically.
I place them in the same directory of the movie file, and with the same name,for example:
movie name : x.avi
so subs name : x.srt 
still, it doesnt work,any idea?

thanks

---

### Post by Dandeloreon on 2008-02-10
This is an easy fix, however it has a few stages, and all involve the Preferences dialoge, which is opened by:

Settings Menu -> Preferences

first is to configure the language, the example i have is for english subtitles by default, but you can get the idea...

in the preferences dialogue go to the "Input/ Codecs" Section.

next in the subtitle languages put, "English,Unknown" ( or whatever else you can do )

next is to configure the subtitle loading/rendering.

For this, you need to check the box in the lower right corner that says Advanced options. after that on the left, go to the following section:

Video -> Subtitles/OSD

modify the option, "Subtitle Autodetection Path", and set it to, "./Subtitles, ./subtitles,."

---

