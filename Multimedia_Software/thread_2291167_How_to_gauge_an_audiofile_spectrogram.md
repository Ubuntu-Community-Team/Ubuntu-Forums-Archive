---
title: "How to gauge an audiofile spectrogram"
date: 2015-08-18
forum: Multimedia Software
---

### Post by shantiq on 2015-08-18
[[IMG]http://s10.postimg.org/ve0ruzi2t/BBC_Proms_2015_Season_1_Prom_36_Prom_36_part.jpg[/IMG]]("http://postimg.org/image/ve0ruzi2t/")
  [COLOR=#696969][FONT=century gothic]using Spek software [in repo]

Obtained with SoX using this line of command: 'sox recording.wav -n spectrogram -o spectrum.png'][/FONT][/COLOR]
[[IMG]http://s11.postimg.org/thphkl6rj/BBC_Proms_2015_Season_1_Prom_36_Prom_36_part.jpg[/IMG]]("http://postimg.org/image/thphkl6rj/")



This is a concert from the BBC Radio 3 website; and they claim 320k quality; but looking around at other [spectrograms of 320k files]("https://www.google.co.uk/search?q=320k+spectrogram+image&biw=1600&bih=703&tbm=isch&tbo=u&source=univ&sa=X&ved=0CCUQsARqFQoTCInc6eW5sscCFaHzcgodAlsPsg&dpr=1#imgrc=_") it seems the image here displays a much lower k in effect.
Now i have little understanding of spectrograms; but what do any of you experienced spectrogram-viewers [!?]   see here
The radio station [broadcasts at 320k ]("http://http://a.files.bbci.co.uk/media/live/manifesto/audio/simulcast/hls/uk/sbr_high/ak/bbc_radio_three.m3u8") but is my recorded concert here genuinely at 320k?

All clever input welcome


thanx   shan

---

### Post by Yellow Pasque on 2015-08-20
Looks like a 17 kHz cutoff, so if I had to guess, they used fdkaac which uses that for the default. [http://wiki.hydrogenaud.io/index.php?title=Fraunhofer_FDK_AAC#Bandwidth](http://wiki.hydrogenaud.io/index.php?title=Fraunhofer_FDK_AAC#Bandwidth)
fdkaac is the best quality AAC encoder on Linux/Android from mu understanding (not counting using encoders through wine like andrew added to abcde).  I don't think there's anything you can do about it short of writing to BBC and trying to get them to use a higher cutoff (20kHz is max) or suggesting they use VBR (which makes more sense to me).. 

If you have fdkaac installed and want to do a test to see whether you can hear a difference (and look at filesize), here are some sample commands:
```
flac -d test.flac -o test.wav
fdkaac -b 320k -w 20000 test.wav -o twenty.m4a
fdkaac -b 320k test.wav -o seventeen.m4a
fdkaac -m 5 test.wav -o vbr.m4a
```

---

### Post by shantiq on 2015-08-21
yes thanx T i think they use fdkaac ; my question arose as the file does not produce the "fuller" graph i see on other 320k

So I have now tested 3 other files 128 192 and 320 on both Spek and SoX
and it appears the 320k broadcast which seemed a little "thin" to me  in fact produces a graph similar to the 192k file here

see for yourselves >>>

**128k**

[[IMG]http://s28.postimg.org/94ddodeix/fb_Kouerien_Folk_Breton_02_Rond_De_Sautro.png[/IMG]]("http://postimg.org/image/94ddodeix/")

[[IMG]http://s28.postimg.org/5nbblefgp/fb_Kouerien_Folk_Breton_02_Rond_De_Sautro.png[/IMG]]("http://postimg.org/image/5nbblefgp/")

**192k**

[[IMG]http://s28.postimg.org/4typss9ft/1_06_Betrayal_Of_The_Cossacks.png[/IMG]]("http://postimg.org/image/4typss9ft/")

[[IMG]http://s28.postimg.org/f1h956vnt/1_06_Betrayal_Of_The_Cossacks_mp3.png[/IMG]]("http://postimg.org/image/f1h956vnt/")

**320k**

[[IMG]http://s28.postimg.org/du7wqpux5/03_The_Gardener.png[/IMG]]("http://postimg.org/image/du7wqpux5/")

[[IMG]http://s28.postimg.org/bj598surt/03_The_Gardener_aac.png[/IMG]]("http://postimg.org/image/bj598surt/")

**and the files from the radio station produced this >>**
and really this is it seems nowhere near 320k quality

[[IMG]http://s10.postimg.org/ve0ruzi2t/BBC_Proms_2015_Season_1_Prom_36_Prom_36_part.jpg[/IMG]]("http://postimg.org/image/ve0ruzi2t/")[[IMG]http://s11.postimg.org/thphkl6rj/BBC_Proms_2015_Season_1_Prom_36_Prom_36_part.jpg[/IMG]]("http://postimg.org/image/thphkl6rj/")

---

### Post by Yellow Pasque on 2015-08-21
> does not produce the "fuller" graph i see on other 320k
You seem to be trying to compare different files (rather than comparing different encodings of the same original file). So yes, they're not going to look like. Also, under the 320k section in your post, you seem to have a .wav file for the sox spectrogram ??

---

### Post by shantiq on 2015-08-21
T  to get a spectrogram in SoX it has to be a wav. decompressing the file from m4a to wav makes NO difference to the graph whatsoever ; i have tested this before uploading these images [explains also why conversely someone turning say a 128 mp3 to a flac  will get EXACTLY the same spectrogram in both files and a fake flac]  ...    it is a Radio file from a website so there is no encoding option ...   it is obtained from the site as an m4a   that is the option available  ...   my question was really to do with whether the file and sound quality were really 320   but it seems they are more like 192
Anyway thank you very much  for input.

---

### Post by Rob Sayer on 2015-08-21
Do you use Mediainfo?  If not, the package name I always install is mediainfo-gui.  It seems like a much easier way to tell the bit rate.

---

### Post by tgalati4 on 2015-08-21
It's possible that the original concert was recorded/Live-streamed at 192 kilobits/second, but the media server simply upscaled to 320k.  Many streaming sites use one content source with transcode-on-the-fly to support low, medium and high bitrates.  If that original source is poor, then streaming at a higher bitrate won't improve the sound or the spectrum.

Try recording several different types of music from the station over different times to see if the quality level varies.

---

### Post by shantiq on 2015-08-22
tgalati    that is exactly the conclusion i had arrived at here
> Many streaming sites use one content source with transcode-on-the-fly to support low, medium and high bitrates
thanx for all your time and help
Not impressed with that trick of theirs
Advertise their stream as HD    and it is **NOT** by a long way
But hey ...    First World Problem
not gonna cry about it :] spotted that a year ago ;    now i know for sure
Shame tho would be nice to have those Prom concerts at a **REAL** higher rate; if i promoted a litre bottle with 75cl of content one would think it wrong


**PS**   the BBC runs 2 streams for Radio 3 [you can test these anywhere you are those are available worldwide]Streams are [here]("http://www.listenlive.eu/uk.html")

one is 128k   ```
http://bbcmedia.ic.llnwd.net/stream/bbcmedia_radio3_mf_p
```
other is 320k HD ```
  http://a.files.bbci.co.uk/media/live/manifesto/audio/simulcast/hls/uk/sbr_high/ak/bbc_radio_three.m3u8
```

Testing the spectrogram at different times it appears there is **NO** difference between the 2 :]

See this   the same piece of music played live [not stored on a website but LIVE]on their 128 and 320 .   i play 128 first then switch to 320 a few seconds later still same piece playing
Check the spectrograms ...    exact same quality  .. ...   there is** NO** difference at all   maybe they sometimes hike the 320 but so far i see no sign of that

                   128 
[[IMG]http://s13.postimg.org/v1uggwes3/128.png[/IMG]]("http://postimg.org/image/v1uggwes3/")
320
[[IMG]http://s13.postimg.org/9qwwcmwnn/320.png[/IMG]]("http://postimg.org/image/9qwwcmwnn/")

---

