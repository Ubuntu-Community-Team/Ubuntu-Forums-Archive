---
title: "How Do I Encode Multiple Mp3 files?"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by Cris987 on 2007-06-09
I want to convert a large number of mp3 files to a lower bitrate, but I dont't know how. LAME only encodes 1 at a time. I found mlame, but I don't know how to install the script (newbie here). 

Can someone teach me how?

Also, by default, an encoder like LAME creates a new file out of the input file after encoding. Is there anyway I can easily change multiple output file names to their original names?

---

### Post by tbroderick on 2007-06-09
If you want a GUI tool, try soundconverter.

For mlame, you can make it executable. Open a terminal;
```

chmod +x /path/to/mlame
```

Then mv or copy to /usr/bin.
```

mv mlame /usr/bin

```

---

