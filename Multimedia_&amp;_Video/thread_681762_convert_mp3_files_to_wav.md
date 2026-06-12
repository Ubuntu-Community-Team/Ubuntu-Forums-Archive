---
title: "convert mp3 files to wav"
date: 2008-01-29
forum: Multimedia &amp; Video
---

### Post by rwrouns on 2008-01-29
I thought I was ripping cds to wav using the following pipeline in Sound Juicer: audio/x-raw-int,rate=44100,channels=2 ! wavenc name=enc ! id3v2mux. File extension: wav.

Turns out I got files named xxx.wav but their properties are type: mp3 audio, MIME type Audio/mp3.  Rhythmbox will play them, but Mac and windows boxes on the network consider them corrupt or unrecognizable file format.  

Two questions: what is the correct pipeline so Sound Juicer will rip proper wav files?

Will Sound Converter bulk transform the files I have now to proper wav files?

---

### Post by zvacet on 2008-01-29
```
sudo apt-get install mpg321 vorbis-tools
```

In synaptic  synaptic install **nautilus-script manager** and n**autilus-script-audio-convert**.

```
nautilus-script-manager enable ConvertAudioFile
```


[This](http://linux.softpedia.com/get/Multimedia/Audio/Perl-Audio-Converter-4392.shtml) is best audio converter I found.It is run from CLI but you can add it to Amarok as plugin and you will have GUI.

---

### Post by rwrouns on 2008-01-29
Thanks, I'll try it.

---

