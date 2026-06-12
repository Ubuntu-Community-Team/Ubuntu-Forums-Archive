---
title: "How to insert subtitles in a DVD?"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by eiffleduarte on 2007-11-24
I want to insert subtitles (from a SRT file) of a given language into a DVD (which does not include this language, of course). Is there a way to do it? Ideally, I'd like to copy the files to my HD, insert the subtitles into the DVD (including an entry for this language in the menus) and then burn the modified files into another disc, without losing frames.

Thanks in advance.

---

### Post by vanadium on 2007-11-24
It is never as simple as that. Inserting subtitles requires you to disassemlbe the DVD into the individual data streams, then author it all again to a new video DVD, including the subtitles. For authoring, including adding srt subtitles, qdvdauthor might be an option, or perhaps also dvdstyler. Doing it with the command line will probably require separate tools for converting the srt titles, but there, you might take a look in the man pages of dvdauthor to see what is possible. I have no experience myself on doing this on Linux, that is why I am being a bit generic here. But perhaps, someone else can step in with more hands-on experience.

---

### Post by eiffleduarte on 2007-11-25
Thanks for the explanation, Vanadium.
I guess I can handle the QDVDAuthor part, but I don't know how to split the DVD into the individual data streams. How do I do it?

---

### Post by yoda-sama on 2007-11-28
You can use DVDDecrypter under WINE and rip using IFO mode.  You'll want to play around in the settings before ripping.  I suggest setting file splitting to 'none'.  And make sure you have stream processing enabled, but you probably don't have to demux each stream, a lot of programs seem to handle the .vob file you get if you just use direct stream copy.  Granted this will just give you the movie, you're original menus are not covered by what I've said.

I trust this is a non-commercial DVD...

---

