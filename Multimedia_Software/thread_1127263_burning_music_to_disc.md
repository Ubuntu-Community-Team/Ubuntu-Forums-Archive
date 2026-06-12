---
title: "burning music to disc"
date: 2009-04-16
forum: Multimedia Software
---

### Post by numbness05 on 2009-04-16
Hi there.

I have a a whole load of albums I want to burn to disc, I have have two questions...

Is it ACC I need to convert them too? and if so what software can I grab to do this...I was told soundkonverter by some one but unfortunately this doesn't seem to offer the option of ACC..

Any body have any ideas please???

Many thanks

---

### Post by SuperSonic4 on 2009-04-16
ACC? I've never heard of ACC, AAC I have (which is decoded with faad2).

You might be able to burn them direct with k3b or brasero if you've got faad2 installed.

I use pacpl converter but it seems to more optimised for the kde desktop

---

### Post by numbness05 on 2009-04-16
Beg your pardon AAC is what I meant...

I do have Brasero and did try but it was telling me that the image or the file was to big despite it only being 37.5MB and the disc being 700MB...

but then again I am a beginner and could quite easily be going about it all the wrong way.. I shall try again.

Could it possibly be that I am trying to burn straight from my external hard drive (please excuse my ignorance) not sure if that would cause difficulties at all?

Many thanks again

---

### Post by SuperSonic4 on 2009-04-16
Burning direct from external hard drive might make it a bit slower in accessing the data but should not make a show-stopping difference

It shouldn't cause any difficulties, are you burning it as a data disc or audio disc? The main reason would be the latter can only have up to 80minutes in time. I'm not up to speed with brasero. If you want to convert to a wav file before burning (this won't improve quality but it will increase file size but some people have reported wav working easier you can do
```
faad <path_to_file>
``` which makes 16&#8208;bit PCM data in wav format by default.

If you want to then convert that to mp3 you can use lame ```
lame -b [COLOR="Red"]160[/COLOR] /path/to/wav/file
```

you can change the red bit to any bitrate you like.

---

### Post by gali98 on 2009-04-16
Why did you make two threads? It just makes things confusing.
If you do need to convert, ffmpeg is quick and pretty robust.
Kory

---

