---
title: "shnsplit, shnconv:  flac options"
date: 2010-03-17
forum: Multimedia Software
---

### Post by WDYSUN on 2010-03-17
Dear Friends

in order to split an entire wave album and get it in flacs I use the following commands 

```

# Wav source
cuebreakpoints file.cue | shnsplit -o flac file.wav

# Wavepack
cuebreakpoints file.cue | shnsplit -o flac file.wv

```

Now I wonder which options (e.g. compression level) are used to create the flacs. 

Does shnplit use the flac software?

Is it possible to pass flac options to shnsplit?

I hope somebody can help.

Best Wishes
Pietro

---

### Post by WDYSUN on 2010-03-22
Has anybody an idea about this?

Pietro

---

### Post by foxy123 on 2010-08-03
> **WDYSUN said:**
> Dear Friends

in order to split an entire wave album and get it in flacs I use the following commands 

```

# Wav source
cuebreakpoints file.cue | shnsplit -o flac file.wav

# Wavepack
cuebreakpoints file.cue | shnsplit -o flac file.wv

```

Now I wonder which options (e.g. compression level) are used to create the flacs. 

Does shnplit use the flac software?

Is it possible to pass flac options to shnsplit?

I hope somebody can help.

Best Wishes
Pietro

I've got an error trying to do it:
```
~/Temp$ cuebreakpoints file.cue | shnsplit -o flac file.wv
shnsplit: warning: none of the builtin format modules handle input file: [file.wv]
shnsplit: error: cannot continue due to error(s) shown above

```

regarding flac options, there is a topic on hydrogen audio:
[http://www.hydrogenaudio.org/forums/index.php?showtopic=79720&st=0&gopid=716731&#entry716731](http://www.hydrogenaudio.org/forums/index.php?showtopic=79720&st=0&gopid=716731&#entry716731)

---

