---
title: "Many small audio files combined into one long one?"
date: 2010-12-26
forum: Multimedia Software
---

### Post by Sarrel on 2010-12-26
I have several audiobooks that are each split into many small chapters, and I would like to string together about ten of them at a time, so that I don't have 60 4-5 minute mp3 files per audiobook.

If I were to do this all by hand, with audacity or something similar, it would get very tedious, so I'd like to know if there's already a program that would do it for me when told which files to string together.

Thank you ahead of time for any help.

---

### Post by Bartender on 2011-03-22
Maybe I shouldn't resurrect old threads, but I've been using Rubyripper.  Under the Preferences tab, there's a checkbox to "Rip CD to a single file".

The suggestion to use Rubyripper may not be very helpful...I read a thread the other day indicating that people are having trouble with Rubyripper and the latest versions of Ubuntu?

I rip the audiobooks as .ogg.  I use this setting in the codecs section

```
-q 0
```

I don't have a good grasp of the quality settings. I believe this tells ogg to rip at the lowest quality it'll go, which is plenty good for audiobooks.  I've tried a few low-quality mp3 settings borrowed from various threads and Ruby refused to rip.  If I knew what entry to use, I'd like to try some mp3 rips.  The existing mp3 string:

```
-V 2 --vbr-new
``` 

makes larger files than ogg.

Sansa Fuze is the preferred player.  It plays .ogg or .mp3.  I've read on Sansa forums that .ogg uses more battery power because there's more processing involved, and that's why I'd like to try some low-quality .mp3 rips.

---

### Post by tgalati4 on 2011-03-22
sox works as well:

sudo apt-get install sox
man sox

---

