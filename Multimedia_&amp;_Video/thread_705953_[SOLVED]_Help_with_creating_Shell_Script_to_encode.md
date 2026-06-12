---
title: "[SOLVED] Help with creating Shell Script to encode audio"
date: 2008-02-23
forum: Multimedia &amp; Video
---

### Post by papafreebird on 2008-02-23
Hello, 
I wasn't sure if this should go in General Help or here in Multimedia so mods if this thread needs moved please do so!

I have two shell scripts that I use to encode audio from avi files to ac3.  The first uses ffmpeg to encode a wav file from the avi.
```
#! /bin/bash

for i in *.avi ; do ffmpeg -i "$i" -ar 48000 "$i.wav" ; done
 


```

The next I use to encode the wav files to ac3 using aften
```

#! /bin/bash

for i in *.wav ; do aften "$i" -acmod 2 -readtoeof 1 -b 192 "$i.ac3" ; done

```

I would like to combine these two into one script and also incorporate **rm *.wav** to delete the wav files after the ac3 encoding is finished.  

Yes I know that I could encode the ac3 directly in ffmpeg but I prefer aften for my ac3 encoding.  Any help you can offer would be greatly appreciated.

Thanks for your time
papafreebird

---

### Post by yabbadabbadont on 2008-02-24
```
#! /bin/bash

for i in *.avi
do
        BASEFILENAME=$(basename $i .avi)

        ffmpeg -i "$i" -ar 48000 "$BASEFILENAME.wav" && \
        aften "$BASEFILENAME.wav" -acmod 2 -readtoeof 1 -b 192 "$BASEFILENAME.ac3" && \
        rm "$BASEFILENAME.wav"
done

```

That should work, but be sure to test it with **copies** of your files before running it on a full set.

---

### Post by papafreebird on 2008-02-24
Hi thanks for your reply!  I tried your script and it worked sort of.  It created a wav and ac3 files  with no names.  Just .wav and .ac3

I edited your script removing the .avi from the basename and then it worked.  Here is the edited working script.
```

#! /bin/bash

for i in *.avi
do
        BASEFILENAME=$(basename "$i")

        ffmpeg -i "$i" -ar 48000 "$BASEFILENAME.wav" && \
        aften "$BASEFILENAME.wav" -acmod 2 -readtoeof 1 -b 192 "$BASEFILENAME.ac3" && \
        rm "$BASEFILENAME.wav"
done

```


Much thanks for your help!
:)

---

