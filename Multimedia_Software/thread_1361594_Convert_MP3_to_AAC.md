---
title: "Convert MP3 to AAC"
date: 2009-12-22
forum: Multimedia Software
---

### Post by numbness05 on 2009-12-22
Hi there guys and girls.

I am having big troubles trying to convert MP3 to AAC to burn on to a disk as an audio CD.

Previously I have used both Soundconverter and SoundKonverter with no problems but it would appear for what ever reason now having come back to use it after having installed the last lot of updates (what ever they were) it has forgotten how to convert to AAC and has left out this option completely leaving me with the option to convert to MP3, OGG or Flac.
If it makes a difference I am currently running Karmic Koala 9.10 and have had several issues with it.

Does any one know what is occurring here or know of another converter that I could possibly try?

Many thanks

---

### Post by ajgreeny on 2009-12-22
I suppose you realise that it is not necessary to convert from mp3 to aac in order to make an audio CD, you can di it direct from mp3.

However, if it is needed for some other reason, I suspect yopu may need to ensure you have at least one of the many encoders available for aac. Do a search in synaptic using just the name filter for aac and several things will show up, I think, some of which are medibuntu supplied, so enable the medibuntu repos if you haven't already done so.
[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by chenxiaolong on 2009-12-22
Could you try installing the package [COLOR="Blue"]libfaac0[/COLOR] and then use sound converter again?

If that doesn't work, you can try converting it using the command line (you don't have to use the slashes; they just separate one long line into multiple lines):
```

ffmpeg \                       #Use ffmpeg to convert
       -i input.mp3 \          #Input file
       -acodec aac \           #Use the aac codec
       -ab 128 \               #Bitrate
       output.aac              #Output file

```

---

### Post by MelDJ on 2009-12-22
> **numbness05 said:**
> Hi there guys and girls.

  Soundconverter and SoundKonverter with no problems but it would appear for what ever reason now having come back to use it after having installed the last lot of updates (what ever they were) it has forgotten how to convert to AAC and has left out this option completely leaving me with the option to convert to MP3, OGG or Flac.


 i am using soundconverter in karmic and it can convert mp3's to aac. the version i use i 1.4.4

---

