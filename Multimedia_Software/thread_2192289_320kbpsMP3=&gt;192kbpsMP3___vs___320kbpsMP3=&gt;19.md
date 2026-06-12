---
title: "320kbpsMP3=&gt;192kbpsMP3   vs   320kbpsMP3=&gt;192kbpsOGG"
date: 2013-12-07
forum: Multimedia Software
---

### Post by czgirb on 2013-12-07
Which better?

Converting **320kbps MP3** into **192kbps MP3 VBR** or
Converting **320kbps MP3** into **192kbps OGG-Vorbis VBR**?

**Thank you.**

---

### Post by tgalati4 on 2013-12-07
You would probably convert 320kbps MP3 into WAV and then compress to whatever format you like.  Which you choose depends on the style of music (classical versus rock) and how you listen to music (ipod/headphones vs 1000-watt stereo system).

Try both compression methods on a single file and listen to them.  OGG gives better performance (smaller size and better acoustic quality) for certain types of music, but few players support it.  If you can't tell the difference (and they will be subtle) then choose based on file size and compatibility with your playback devices.

---

### Post by bachtobach on 2013-12-07
You shouldn't ever convert from lossy to lossy. MP3 to anything is always going to result is worse quality, no matter what settings/bitrates you choose for the target format. If you want to convert to a lower bitrate or different format then you should only do it from a lossless source, like .wav or .flac. 

At 192kbps OGG-vorbis would be better probably but I'm not sure what you mean by 192kbps VBR (VBR uses presets, there is no fixed bitrate, it changes throughout the file). At higher bitrates, like V0 (vbr) you probably wouldn't tell much difference between that and any ogg-vorbis encoding.

---

### Post by cryptotheslow on 2013-12-07
Bear in mind that some audio players can get really confused with VBR mp3 files showing very odd track durations and making tracks un-seekable. I have this problem with Rhythmbox for one.

As bachtobach says downsampling mp3 to mp3 will give pretty horrible results. I've done it before and the result is a really muddy sounding mess - high frequency sounds like cymbals became all swishy whilst the lower frequencies lost any real definition at all. But that is a purely subjective thing, a lot of people don't seem to notice the difference. Try doing a few tracks both ways and listen to all three versions back to back and go with what works for you.

---

### Post by shantiq on 2013-12-08
320 k mp3 is ok for an mp3 player
why make the file smaller?    to save space   ...    surely these days players are big enough to handle many 320 

if you are using these on a computer please do yourself a favour and store them in lossless    probably flac


my samsung   which is only one gig   and old now [IMG]http://cdn.cnet.com.au/story_media/240062360/samsung-yp-u2_1.jpg[/IMG]
will play mp3 ogg and wave   ....     i have tried all of those   and wave is overkill apart from being so big of course

out of ogg and mp3 there is little to say    ogg goes to 499k if you want it too   and mp3 to 320k     but really on those types of devices   it matters little

i agree with the other guys one more conversion will not help quality

i suggest you remain with 320   it is fine for portable players...   but for computers    to me at least anathema    ps   many players can handle flac these days too ; that sounds like a good plan to me

---

### Post by Yellow Pasque on 2013-12-08
> **tgalati4 said:**
> You would probably convert 320kbps MP3 into WAV and then compress to whatever format you like.

I don't think converting to WAV first will help. The .wav won't have any extra audio information than the original mp3 does. You can't magically gain audio quality going from lossy -> lossless

---

### Post by FakeOutdoorsman on 2013-12-08
> **czgirb said:**
> Which better?

Converting **320kbps MP3** into **192kbps MP3 VBR** or
Converting **320kbps MP3** into **192kbps OGG-Vorbis VBR**?

Why re-encode in the first place?

If you must re-encode, then see:
[list]
[*][Recommended Vorbis Encoding Settings](http://wiki.hydrogenaudio.org/index.php?title=Recommended_Ogg_Vorbis#Recommended_Encoder_Settings)
[*][Recommended LAME Encoding Settings](http://wiki.hydrogenaudio.org/index.php?title=LAME#VBR_.28variable_bitrate.29_settings)
[/list]

They are both decent encoders. You can perform an ABX test to see which one sounds better to you.

> **Temüjin said:**
> I don't think converting to WAV first will help. The .wav won't have any extra audio information than the original mp3 does. You can't magically gain audio quality going from lossy -> lossless
+1

---

