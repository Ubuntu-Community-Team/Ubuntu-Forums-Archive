---
title: "Encoding MP3 to OGG"
date: 2009-06-11
forum: Multimedia Software
---

### Post by Brinstar on 2009-06-11
Can someone advise me on whether how to go about re-encoding my MP3 collection into OGG? at the moment the files are becoming 2-3 times bigger, which is sort of defeating the point :S

---

### Post by logos34 on 2009-06-11
why would you want to do that? The general rule is to avoid lossy-to-lossy conversion whenever possible (because of sound quality degradation). Most media players support mp3 as long as you add the right codec pkg (e.g. ubuntu-restricted-extras).  Others like vlc and xine-based engines already include it

---

### Post by stumbleUpon on 2009-06-11
There is a script in this thread

[http://ubuntuforums.org/showthread.php?t=1110872](http://ubuntuforums.org/showthread.php?t=1110872)

You might find it useful, although i am not sure about converting mp3 to ogg. The original idea there was to convert rm to mp3. But it might work if you tweak around a little with the script.

EDIT: The script (convert2 as modified by andrew.46) works perfectly well for converting mp3 to ogg as well. Just make sure you have vorbis-tools installed (sudo aptitude install vorbis-tools) before converting mp3 to ogg.

The file size did go up by about 17% for file that i used.

---

### Post by Brinstar on 2009-06-11
> **logos34 said:**
> why would you want to do that? The general rule is to avoid lossy-to-lossy conversion whenever possible (because of sound quality degradation). Most media players support mp3 as long as you add the right codec pkg (e.g. ubuntu-restricted-extras).  Others like vlc and xine-based engines already include it

why? for freedom from licensed crap like mp3, thats why. if you didnt notice, ubuntu plays ogg out of the box, but NOT mp3, theres a good reason for that.

> **stumbleUpon said:**
> There is a script in this thread

[http://ubuntuforums.org/showthread.php?t=1110872](http://ubuntuforums.org/showthread.php?t=1110872)

You might find it useful, although i am not sure about converting mp3 to ogg. The original idea there was to convert rm to mp3. But it might work if you tweak around a little with the script.

EDIT: The script (convert2 as modified by andrew.46) works perfectly well for converting mp3 to ogg as well. Just make sure you have vorbis-tools installed (sudo aptitude install vorbis-tools) before converting mp3 to ogg.

The file size did go up by about 17% for file that i used.

thanks but i think i have answered my own question now, i am just using Bonkenc from a windows pc (heh, ironic you might think given what i just said above) setting the quality at 3.0. by the way, ogg is very good at that quality.

---

### Post by logos34 on 2009-06-11
> **Brinstar said:**
> why? for freedom from licensed crap like mp3, thats why. if you didnt notice, ubuntu plays ogg out of the box, but NOT mp3, theres a good reason for that.

I'm well aware if that (note the link in my signature to FSF's "Play OGG" campaign)...I'm a proponent of open-source codecs (especially ogg vorbis vs. mp3), [but not at the price of sound quality]("http://wiki.hydrogenaudio.org/index.php?title=Transcoding") (self-defeating).  Most new linux users switch to ogg or flac for future cd rips, and keep their existing mp3s as is.

---

### Post by Gen2ly on 2009-06-11
Last I heard you could convert mp3 to ogg without losing lossy but cannot do it the other way.

---

### Post by Brinstar on 2009-06-12
> **Dirk.R.Gently said:**
> Last I heard you could convert mp3 to ogg without losing lossy but cannot do it the other way.

you heard right. i converted my mp3s back to wav, then to ogg, and tried directly converting to ogg (from mp3). the result was the same.

---

### Post by MartyBuntu on 2009-06-12
There's an app called **OggConvert** in the repositories. It's the GUI frontend I use to convert .wav and .flac to OGG.
In the GUI, there's a slider to adjust quality/file size.

---

