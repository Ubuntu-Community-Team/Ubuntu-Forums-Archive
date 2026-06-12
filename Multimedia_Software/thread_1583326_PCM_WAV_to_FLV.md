---
title: "PCM WAV to FLV"
date: 2010-09-27
forum: Multimedia Software
---

### Post by Scooter89 on 2010-09-27
Hello! I am trying to convert a PCM WAV file to FLV using ffmpeg via terminal. I'm a newbie with this type of conversion so I'm struggling. I'm hoping someone can help me along. This is what I have so far: ffmpeg -i test1.wavpcm test2.flv

I then get an error saying "<incorrect codec parameters ?>".

---

### Post by ron999 on 2010-09-27
Hi
This command should do it:-
```
ffmpeg -i test1.wavpcm -vn -acodec copy test2.flv
```

---

### Post by andrew.46 on 2010-09-28
Mind you an flv container can take a variety of audio codecs, I guess the most common would be aac or mp3. The gory details can be seen here:

[http://en.wikipedia.org/wiki/Flash_Video#Media_type_support](http://en.wikipedia.org/wiki/Flash_Video#Media_type_support)

With no codec specified FFmpeg defaults, at least on my own setup, to mp3. Can you provide the full command and full terminal output for your conversion?

Andrew

---

### Post by Scooter89 on 2010-09-29
Alrighty, I tried the suggested code and it displayed the same error as before.

Here's my goal: To start with a WAV, convert to WAVPCM (using sox), then convert to FLV(using ffmpeg). Here are the code snippets I have created thus far:

WAV to WAVPCM (sox) Note: This works.
```
sox test1.wav -e signed test2.wavpcm rate 16k
```

WAVPCM to FLV (ffmpeg) Note: This does not work.
```
ffmpeg -i test2.wavpcm -vn -shortest -ar 16000 -ab 8000 -acodec libspeex -y test3.flv
```

When converting from WAVPCM to FLV, the FLV file is completely silent. No errors or anything just no sound at all when playing the file. Hmmmm....

---

### Post by andrew.46 on 2010-09-29
Hi scooter,

I am still a little puzzled as to why you are not happy with mp3 or aac in your flv container? However if you are set on wav the following will help:

```

ffmpeg -i *input.wav* -acodec adpcm_swf *output.flv*

```

where of course you will need to alter *input.wav* and *output.flv* to suit your needs. **Edit:** Mind you after a bit of reading up it is almost worthwhile to use the famously reverse engineered Nellymoser codec since this caused [so much fuss]("http://en.wikipedia.org/wiki/Nellymoser_Asao_Codec") in its time:

```

ffmpeg -i *input.wav* -acodec nellymoser -ac 1 *output.flv*

```

This will also live quite well in an flv container.

All the best,

Andrew

---

