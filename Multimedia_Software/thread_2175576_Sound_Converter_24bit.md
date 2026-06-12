---
title: "Sound Converter 24bit?"
date: 2013-09-19
forum: Multimedia Software
---

### Post by Dapilot1 on 2013-09-19
I was converting the soundtracks from the humble bundles I have gotten and ran into tons of errors.
It seems 24 bit flac files will not convert. I want to make them oggs, but have tried flac and wav as well.
Also it is kinda stupid that it deletes the original if it gets an error, leaving you with a 0 byte file instead.

So is there a way to get Sound Converter to handle 24 bit files?
Is there a way to down sample to 16 bit while keeping all the goodies like album art?

---

### Post by Yellow Pasque on 2013-09-20
Tried avconv instead?

---

### Post by shantiq on 2013-09-21
Hi Pilot




short answer   &#9658;&#9658;&#9658;    change to your directory  ```
cd nameofdirectory
```  and run


```

  for f in *.flac; do sox "$f" -C 9  "${f%.flac}.ogg"  ;  done
```

[COLOR=#000000][ALL TAGS ARE KEPT but not cover art; puddletag/easytag will correct this]
[/COLOR]
&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;    

more detailed:

you can go from 24-bit flac to lossy wavpack this way and keep 24-bit in the lossy file [sudo apt-get install wavpack]
Has you can see it goes to wav first so the tagging goes but can retag with puddletag/easytag etc...



KEEP 24-BIT [flac to lossy wavpack]


```
ffmpeg -i file.flac -acodec pcm_s24le -ar 48000 output.wav \
&& wavpack -b4x output.wav  && rm output.wav
```






OR ogg

if you want ogg use sox [ALL TAGS ARE KEPT but not cover art; puddletag/easytag will correct this]


> sox file.flac -C 9 file.ogg -C 1 to -C 10 [499k] your options here 320k is 9




in bulk
and that is really the answer to your question i suppose




```

  for f in *.flac; do sox "$f" -C 9  "${f%.flac}.ogg"  ;  done



```

---

### Post by Dapilot1 on 2013-09-30
Thank you. That does work to convert the files, but I'm a little sad that the sound converter app can't be fixed.

---

