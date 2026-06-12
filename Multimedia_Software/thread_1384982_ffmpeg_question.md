---
title: "ffmpeg question"
date: 2010-01-19
forum: Multimedia Software
---

### Post by sgriggly on 2010-01-19
hello i'm converting various video files (the ones i've tried so far were .mpeg and .wmv, which both gave me the same error message) to 3gp format to play on my phone using ffmpeg. the error message i keep getting relates to screen size, and references the H.263 codec and its inability to convert it. from what i gather, i have to set the screen size... how to do it? 

"The specified picture size of 640x480 is not valid for the H.263 codec. Valid sizes are 128x96....

Try H.263+. Error while opening codec for output stream #0.0 - maybe incorrect parameters..."

---

### Post by andrew.46 on 2010-01-20
Hi sgriggly,

The full message was probably:

```
Valid sizes are 128x96, 176x144, 352x288, 704x576, and 1408x1152. Try
H.263+.
```

Have you tried adding one of these sizes into your commandline? For example:

```
ffmpeg -i <inputfile> -vcodec h263 **[COLOR="Red"]-s 352x288[/COLOR]** -acodec etc etc.... <outputfile>
``` 

All the best,

Andrew

---

