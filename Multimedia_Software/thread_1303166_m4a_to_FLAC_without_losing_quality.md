---
title: "m4a to FLAC without losing quality?"
date: 2009-10-27
forum: Multimedia Software
---

### Post by Captain_Falafel on 2009-10-27
Is there a way to convert Apple lossless music files, m4a, to FLAC files without losing quality, and if so, how?

Thanks in advance.

---

### Post by mc4man on 2009-10-28
The easiest way to convert and preserve tags is to use soundkonverter.

don't use too much so haven't explored the settings,  using the 'copy directory structure' for output seemed to be the easiest way to keep track names, ect.

You'll also need mplayer installed and then open sk -> settings -> configure sk -> backends.

Set the decoder for m4a to mplayer and in the main page set output as noted.

I then close and re-open sk to make sure the new settings take.

Then just add a file(s) or a folder and click start. You'll find the conversions in home/soundkonveter by default

edit:
there should be no quality loss - apple lossless -> wav -> flac

---

### Post by Captain_Falafel on 2009-10-28
> **mc4man said:**
> The easiest way to convert and preserve tags is to use soundkonverter.

don't use too much so haven't explored the settings,  using the 'copy directory structure' for output seemed to be the easiest way to keep track names, ect.

You'll also need mplayer installed and then open sk -> settings -> configure sk -> backends.

Set the decoder for m4a to mplayer and in the main page set output as noted.

I then close and re-open sk to make sure the new settings take.

Then just add a file(s) or a folder and click start. You'll find the conversions in home/soundkonveter by default

edit:
there should be no quality loss - apple lossless -> wav -> flac

Thank you! I usually don't like anything to do with Apple, so I wanted to convert to open source flac :popcorn:

---

### Post by vinutux on 2009-10-28
ogg is another lossy opensource format and there is a tool called oggvonvert to convert it

---

