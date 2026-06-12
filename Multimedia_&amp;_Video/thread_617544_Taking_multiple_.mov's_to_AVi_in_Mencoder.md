---
title: "Taking multiple .mov's to AVi in Mencoder"
date: 2007-11-19
forum: Multimedia &amp; Video
---

### Post by Gritty on 2007-11-19
I was wonder if someone would give me a hand on the best way to convert multiple quicktime files to AVI so as I will be able to play on my media center which does not support mov's?  

I can convert 1 with no trouble but want to be able to convert many at a time.  The command

"mencoder -ovc copy -oac pcm -o output.avi filename.mov"  works fine for one to one, but I would like many to many.  Any ideas would be greatly appreciated.

---

### Post by killermist on 2008-01-17
Provided that your supplied command works as you want it to, then you should be able to wrap the command in a for loop in bash.

Example:
```
for file in *.mov; do mencoder -ovc copy -oac pcm "$file" -o "$file.avi"; done
```

The quoting on the "$file" and "$file.avi" passed to the command is important, elsewise if the selected files have spaces or other special characters, they'll muck up mencoder's command line arguments, being turned into multiple elements that it thinks should be parsed as files but aren't and fail.

There are quite a few places that talk about for loops and how they work in bash.  If you get stuck, ask for clarification, and I'll try to find you something suitable.

---

